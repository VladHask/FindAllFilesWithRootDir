/* Находим все файлы
Реализовать логику метода getFileTree, который должен в директории root найти список всех файлов включая вложенные.
Используйте очередь, рекурсию не используйте.
Верните список всех путей к найденным файлам, путь к директориям возвращать не надо.
Путь должен быть абсолютный.
*/

import java.io.File;
import java.io.IOException;
import java.util.*;

public class Solution {
    public static List<String> getFileTree(String root) throws IOException {
        List<String> filelist = new ArrayList<>();
        Queue<File> q = new LinkedList<>();
        q.add(new File(root));
        while(!(q.isEmpty())){
            File child = q.remove();
            if (child.isDirectory()){
                for (File f : child.listFiles())
                    q.add(f);
            }else filelist.add(child.getAbsolutePath());
        }
        return filelist;

    }

    public static void main(String[] args) throws IOException{

       List<String> list  = getFileTree("C:\\temp");
       for(String s : list)
       {
           System.out.println(s);
       }
    }
}

