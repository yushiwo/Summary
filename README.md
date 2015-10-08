# Summary
Android一些小知识点总结

#1 AsyncTask 和 Thread 区别
（1）AsyncTask是封装好的线程池，比起Thread+Handler的方式，AsyncTask在操作UI线程上更方便，因为onPreExecute()、onPostExecute()及更新UI方法onProgressUpdate()均运行在主线程中，这样就不用Handler发消息处理了；

（2）我不太同意封装好就会影响性能的说法，在我实际的运用中，真正的缺点来自于AsyncTask的全局线程池只有5个工作线程，也就是说，一个APP如果运用AsyncTask技术来执行线程，那么同一时间最多只能有5个线程同时运行，其他线程将被阻塞（注：不运用AsyncTask执行的线程，也就是自己new出来的线程不受此限制），所以AsyncTask不要用于多线程取网络数据，因为很可能这样会产生阻塞，从而降低效率。

建议好好阅读这篇文章：http://blog.csdn.net/mylzc/article/details/6784415
