<h1>yolov3環境架設筆記</h1>
<p>
<p>有鑑於每次重新架設yolo環境都要重新找之前看的網站或是書籍，而網路上的資料零零散散，常常需要翻很多個網站看有無漏掉的細節，因此決定自己寫一個環境架設的筆記來記錄架環境的過程，如有寫錯的地方歡迎不吝賜教。
<p>
<h2>第一步：安裝cuda與cudnn</h2>
<p>
<p><h3>1.安裝CUDA</h3></p>
<p>第一步：到<a href="https://developer.nvidia.com/cuda-toolkit-archive">CUDA官網</a>點選自己需要的CUDA版本，個人目前使用10.1版</p>
<img src="https://github.com/lhmjimmy/Yolov3-/blob/master/cuda_v.PNG">
<p>第二步：依照下圖進行勾選，並點擊Download，檔案約2.5G，可以先去泡個泡麵再回來繼續安裝~</p>
<p>註：載好後直接點擊安裝，基本上一路下一步到底就好了，安裝了56次好像沒遇過安裝過程卡住的狀況哈哈</p>
<p><img src="https://github.com/lhmjimmy/Yolov3-/blob/master/cuda_install.PNG"></p>
<p>第三步：安裝好之後叫出你的cmd並輸入nvcc --version確認，如果有顯示如下圖(最後一行會顯示你系統目前使用的Cuda版本)，代表安裝成功了~恭喜你~!</p>
<p><img src="https://github.com/lhmjimmy/Yolov3-/blob/master/cuda_checkv.PNG"></p>







<p><h3>2.安裝cudnn</h3></p>
<p>第一步：到<a href="https://developer.nvidia.com/cudnn">CUDA官網下載cudnn的地方</a>，點選Download cuDNN</p>
<p>註:下載cudnn需要註冊Nvdia帳號並登入才能下載，沒有帳號的去註冊一個就可以下載了~!</p>
<img src="https://github.com/lhmjimmy/Yolov3-/blob/master/Download%20cuDNN.PNG">
<p>第二步：勾選 I Agree To the Terms of the cuDNN Software License Agreement，勾選後點擊下方的Archived cuDNN Releases進到選擇版本頁面</p>
<img src="https://github.com/lhmjimmy/Yolov3-/blob/master/cudnn_releases.PNG">
<p>第三部：點選自己需要的cudnn版本，個人目前使用7.6.2版，並根據自己的系統去選擇要下載的檔案點擊下載。</p>
<img src="https://github.com/lhmjimmy/Yolov3-/blob/master/cudnn_version.PNG">

