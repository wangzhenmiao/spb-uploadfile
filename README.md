# spb-uploadfile

一、文件上传前端实现

        <form class="form-horizontal" action="upload" enctype="multipart/form-data" method="post">
        
1、form表单中，action="upload"+method="post"，所以路径为 /upload,请求类型为post,对应controller: @PostMapping(value="/upload")

2、enctype="multipart/form-data"，浏览器将采用二进制流的方式处理表单数据

二、文件上传pom依赖

1、commons-fileupload


二、文件上传后端实现

1、MultipartFile

上传文件会自动绑定到MultipartFile中

import org.springframework.web.multipart.MultipartFile;

类的主要方法：

file.isEmpty()：文件是否为空

file.getOriginalFilename()：获取文件名

file.transferTo(new File(path+File.separator+ filename))：文件保存到制定路径

四、上传文件的大小

1、默认大小是1MB,如果上传大于1MB的，会报错。如下：

        Maximum upload size exceeded; nested exception is java.lang.IllegalStateException: 
        org.apache.tomcat.util.http.fileupload.FileUploadBase$SizeLimitExceededException: 
        the request was rejected because its size (19172758) exceeds the configured maximum (10485760)

2、配置文件中增加：

        # Single file max size
        spring.servlet.multipart.maxFileSize=50MB
        # All files max size
        spring.servlet.multipart.maxRequestSize=50MB

五、通过对象上传文件

1、ModelAttribute

         @RequestMapping(value="/register")
                     public String register(HttpServletRequest request,
                                   @ModelAttribute User user,
                                   Model model)throws Exception{
                                   
@ModelAttribute 注解将表单参数绑定到User对象，前端html的元素的name都是对象的属性

在controller的方法中，使用@ModelAttribute 把表单参数绑定到方法的入参对象

2、Model


    @RequestMapping(value="/register")
     public String register(HttpServletRequest request,
                            @ModelAttribute User user,
                            Model model)throws Exception{
                                   
函数体内执行完之后，可以

// 将用户添加到model
            model.addAttribute("user", user);
把用户信息放到model中，跳转到html中使用
        
        <td th:text="${user.username}">用户名</td>
    