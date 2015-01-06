UploadFileUtil
==============

基于org.apache.commons.fileupload（http://commons.apache.org/proper/commons-fileupload ）。对其进行了一些封装，简单易用。  
由于上传文件时，需要设定method=“post”，并且enctype=“multipart/form-data”。
所以，服务端需要做更多的工作来获取文件，也不能使用通常的方法来获取请求参数。
UploadFileUtil就是为了简化这些工作，并且让你更好的专注业务逻辑而非这些细节。
内部逻辑很简单，分而治之，阅读起来会更加清晰明了。

调用UploadFileUtil的getUploadFile2Map(request, response)，剩下的一起都交给他就好了。
他会返回一个Map结构，请求参数名称为key，即可取出对应的value。文件也不例外。

所有的文件上传过程都不用再花费过多的精力，只需要
      UploadFileUtil uf = new UploadFileUtil();
			Map parameter = uf.getUploadFile2Map(request, response);
parameter中包含了全部的上传参数以及文件。

相关参数设置：

Maxsize ：文件最大尺寸限制;    //默认值为 4 * 1024 * 1024 ; 4MB
allowFileTypes ： 允许上传的文件格式; //默认为图片上传 {"jpg", "jpeg", "png","JPG", "JPEG", "PNG"};

