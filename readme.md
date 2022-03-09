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
<p>&emsp;&emsp;個人是裝2022版，之前看到爬文有人推2015跟2017比較不會出錯，不過我用2022除錯了一下也順利的架設好了，所以這邊分享一下Visual Studio2022的安裝方法，如果有大大有更方便的安裝方法歡迎跟我分想一下，之前為了這Visual Studio的部分卡了兩天差點放棄ಥ_ಥ</p>
<p>1.：到<a href="https://visualstudio.microsoft.com/zh-hant/downloads/">Visual Studio官網</a>點選社群下方的免費下載按鈕，個人目前使用2022版，下載完後直接點擊安裝</p>
<p><img src="https://github.com/lhmjimmy/Yolov3-/blob/master/VisualStudio_download.PNG"></p>
<p>2.：安裝時基本上只要一直下一步就好，直到下方圖片的畫面。勾選1跟2之後，點擊3進行安裝</p>
<p>註：這邊是選擇要安裝的套件，可以根據自己開發需求選擇要安裝的套件，若不知道安裝什麼就先照著下方圖片勾選，其他套件有需後續都可以繼續安裝</p>
<p><img src="https://github.com/lhmjimmy/Yolov3-/blob/master/VisualStudio_check.PNG"></p>
<h2>第三步：安裝OpenCV</h2>
<p>1.到<a href="https://opencv.org/releases/">OpenCV官網下載要的OpenCV版本</a>，個人目前使用3.4.16</p>
<p>2.下載好後解壓縮到自己要的地方，我是解壓縮在C槽根目錄C:\opencv-3.4.16-vc14_vc15(解壓縮的位置要記得，後面會使用到)</p>
<h2>第四步：下載darknet並解壓縮</h2>
<p>1.到github<a href="https://github.com/AlexeyAB/darknet">下載darknet</a></p>
<p><img src="https://github.com/lhmjimmy/Yolov3-/blob/master/darknet_download.PNG"></p>
<p>2.下載好之後解壓縮到自己要的位置，我是解壓縮在我的G槽G:\darknet-master</p>
<p>3.打開在darknet-master資料夾中的build資料夾，再打開build資料夾中的darknet資料夾，應該會看到如下畫面</p>
<p><img src="https://github.com/lhmjimmy/Yolov3-/blob/master/darknet_cudav.PNG"></p>
<p>4.將畫面中圈起來的檔案拖入你要的編輯器中，我是使用vscode，並修改下列兩處，將CUDA改成自己的版本，例如我的是10.1就改成10.1</p>
<p>註：因為版本的更動行數也許不一定跟我一樣，如果按照圖片上的行數找不到請善用ctrl+F</p>
<p><img src="https://github.com/lhmjimmy/Yolov3-/blob/master/darknet_version1.PNG"></p>
<p><img src="https://github.com/lhmjimmy/Yolov3-/blob/master/darknet_version2.PNG"></p>
<p>5.到C:\Program Files (x86)\MSBuild\Microsoft.Cpp\v4.0\BuildCustomizations確認是否有以下檔案，如果有代表成功了</p>
<p><img src="https://github.com/lhmjimmy/Yolov3-/blob/master/darknet_filecheck.PNG"></p>
如果沒有這些檔案請到C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v10.1\extras\visual_studio_integration\MSBuildExtensions中把裡面的4個檔案copy到C:\Program Files (x86)\MSBuild\Microsoft.Cpp\v4.0\BuildCustomizations中。(路徑通常不會有差異，路徑中通常只會有版本號跟我不一樣v10.1)
<p></p>
<p>6.到3.提到的build資料夾下的darknet資料夾，並用vs2022將darknet.sln</p>
