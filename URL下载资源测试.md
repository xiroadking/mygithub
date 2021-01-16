#### URL下载资源 测试

```
package com.example.springbootdemo.test.network;

import java.io.FileOutputStream;
import java.io.IOException;
import java.io.InputStream;
import java.net.HttpURLConnection;
import java.net.URL;

/**
 * URL下载资源 测试
 *
 * @author 瞎折腾
 */
public class TestUrlDown {

    public static void main(String[] args) throws IOException {
        // 下载地址 下载收费的音乐URL地址
        URL url = new URL("https://m801.music.126.net/20210116165416/2bea3a21aca5419ef93648676bec423c/jdyyaac/015a/5653/0f59/60dfe1efe5a91f3dca97834c1279e9c3.m4a");
        // 连接到这个资源
        HttpURLConnection urlConnection = (HttpURLConnection) url.openConnection();
        // 输入流
        InputStream inputStream = urlConnection.getInputStream();
        // 文件输出流
        FileOutputStream fos = new FileOutputStream("down_song.m4a");
        // 写出文件
        byte[] buffer = new byte[1024];
        int len;
        while ((len = inputStream.read(buffer)) != -1) {
            fos.write(buffer, 0, len);
        }
        // 关闭连接
        fos.close();
        inputStream.close();
        urlConnection.disconnect();
    }

}
```