<h1>yolov3環境架設筆記</h1>
<p>
<p>&emsp;&emsp;大家好~我是吉米，環境架設對於大部分新手工程師們常常是一場惡夢(有時候老手也是XD)，在網路上爬文半天結果忽略某個細節導致後面又要回頭除錯，一天就這樣過去了ಥ_ಥ，在這邊給剛接觸yolo需要架環境的工程師們參考，省時間並少走一些彎路~目前還在慢慢更新中，CUDA跟cudnn的配置已經寫完了~後續會繼續補上</p>
<p>&emsp;&emsp;有鑑於每次重新架設yolo環境都要重新找之前看的網站或是書籍，而網路上的資料零零散散，常常需要翻很多個網站看有無漏掉的細節，因此決定自己寫一個環境架設的筆記來記錄架環境的過程，如有寫錯的地方歡迎不吝賜教。
<p>
<h2>第一步：安裝cuda與cudnn並配置環境</h2>
<p>
<p><h3>1.安裝CUDA</h3></p>
<p>第一步：到<a href="https://developer.nvidia.com/cuda-toolkit-archive">CUDA官網</a>點選自己需要的CUDA版本，個人目前使用10.1版</p>
<img src="https://github.com/lhmjimmy/Yolov3-/blob/master/cuda_v.PNG">
<p>第二步：依照下圖進行勾選，並點擊Download，檔案約2.5G，可以先去泡個泡麵再回來繼續安裝~</p>
<p>註：載好後直接點擊安裝，基本上一路下一步到底就好了，安裝了56次好像沒遇過安裝過程卡住的狀況哈哈</p>
<p><img src="https://github.com/lhmjimmy/Yolov3-/blob/master/cuda_install.PNG"></p>
<p>第三步：安裝好之後叫出你的cmd並輸入nvcc --version確認，如果有顯示如下圖(最後一行會顯示你系統目前使用的Cuda版本)，代表安裝成功了~恭喜你~!</p>
<p><img src="https://github.com/lhmjimmy/Yolov3-/blob/master/cuda_checkv.PNG"></p>
<p>或是查看環境變數中的系統變數是否有這兩行。V幾會根據你下載的版本而定，不要看到數字不一樣就覺得我是不是裝錯了，請放心~</p>
<p><img src="https://github.com/lhmjimmy/Yolov3-/blob/master/cuda_env.PNG"></p>


<p><h3>2.安裝cudnn</h3></p>
<p>第一步：到<a href="https://developer.nvidia.com/cudnn">CUDA官網下載cudnn的地方</a>，點選Download cuDNN</p>
<p>註:下載cudnn需要註冊Nvdia帳號並登入才能下載，沒有帳號的去註冊一個就可以下載了~!</p>
<img src="https://github.com/lhmjimmy/Yolov3-/blob/master/Download%20cuDNN.PNG">
<p>第二步：勾選 I Agree To the Terms of the cuDNN Software License Agreement，勾選後點擊下方的Archived cuDNN Releases進到選擇版本頁面</p>
<img src="https://github.com/lhmjimmy/Yolov3-/blob/master/cudnn_releases.PNG">
<p>第三步：點選自己需要的cudnn版本，個人目前使用7.6.2版，並根據自己的系統去選擇要下載的檔案點擊下載。</p>
<img src="https://github.com/lhmjimmy/Yolov3-/blob/master/cudnn_version.PNG">
<p>第四步：下載完後解壓縮到自己要的地方，我自己是解壓縮在C槽根目錄下，解壓縮後會得到一個資料夾</p>
<p><img src="https://github.com/lhmjimmy/Yolov3-/blob/master/cudnn_unzip.PNG"></p>
<p>第五步：這邊的操作比較複雜!!!請仔細看 不要因為複雜就跳過喔~這個步驟沒做後面架環境會有問題</p>
<p>註：假設版本跟我一樣且都是解壓縮在C槽根目錄下方的話，路徑可以照貼找到檔案，別連檔案名稱都複製貼上喔~複製路徑就好</p>
<p><h4>1.把 C:\cudnn-10.2-windows10-x64-v7.6.5.32\cuda\bin\cudnn64_7.dll 複製到 C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v10.1\bin中</h4></p>
<p><h4>2.把 C:\cudnn-10.2-windows10-x64-v7.6.5.32\cuda\include\cudnn.h 複製到 C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v10.1\include中</h4></p>
<p><h4>3.把 C:\cudnn-10.2-windows10-x64-v7.6.5.32\cuda\lib\x64\cudnn.lib 複製到 C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v10.1\lib\x64中</h4></p>
<p>
<p><h3>恭喜你~以上步驟都順利完成的話~你的cuda 與cudnn配置就完成囉~</h3></p>
<h2>第二步：安裝Visual Studio</h2>
