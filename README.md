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

2、

    