
<!-- vim-markdown-toc GFM -->

* [C++ 文件操作](#c-文件操作)

<!-- vim-markdown-toc -->
# C++ 文件操作

<font size=4><b>
		fstream 读写操作  
		ofstream 写操作  
		ifstream 都操作  
</b></font>  

使用

```
void ReadWrite() {                       
	ofstream outfile("test.txt",ios::out);   // 输入流
	ifstream readfile("test.txt",ios::in);   // 定义输出流
                                         
	if(!readfile.is_open()) {              
		cout << "open file error" << endl;     // 判断文件是否打开成功 一般判断一个就可以了
		return;                              
	}                                      
	                                       
	                                       
	outfile << "hello world" << endl;        // 写入字符
                                         
	                                       
	string buf;                            
	while(getline(readfile,buf)) {           // 读取字符
		cout << buf << endl;                 
	}                                      
	outfile.close() ;                      
	readfile.close();                      
}                                        

```
打开方式
|打开方式|描述|
|:-|:-:|
|ios::app|追加模式。所有写入都追加到文件末尾|
|ios::ate|文件打开后自动定位到文件末尾
|ios::in|打开文件用于读取
|ios::trunc|设置该文件已经存在，其内容将在打开文件之前被截断，把文件长度设置为0
您可以把以上两种或两种以上的模式结合使用。例如，如果您想要以写入模式打开文件，并希望截断文件，以防文件已存在，那么您可以使用下面的语法：
```
ofstream outfile;
outfile.open("file.dat", ios::out | ios::trunc );

```

<font size=4><b>关闭文件</b></font>  
```
void close();
```

