<h1>yolov3環境架設筆記_win10</h1>
<p>
<p>&emsp;&emsp;大家好~我是吉米，環境架設對於大部分新手工程師們常常是一場惡夢(有時候老手也是XD)，在網路上爬文半天結果忽略某個細節導致後面又要回頭除錯，一天就這樣過去了ಥ_ಥ，在這邊給剛接觸yolo需要架環境的工程師們參考，省時間並少走一些彎路~目前還在慢慢更新中，CUDA跟cudnn的配置已經寫完了~後續會繼續補上</p>
<p>&emsp;&emsp;有鑑於每次重新架設yolo環境都要重新找之前看的網站或是書籍，而網路上的資料零零散散，常常需要翻很多個網站看有無漏掉的細節，因此決定自己寫一個環境架設的筆記來記錄架環境的過程，如有寫錯的地方歡迎不吝賜教。
 
<p>在此特別感謝之爬文時給了很大幫助的幾位前輩</p>
<p>第一位是大陸知乎上的小新哥，下面是他知乎上的連結</p>
<p>https://www.zhihu.com/people/zzd-65-78</p>
<p>第二位是Medium上的李謦伊小姐姐，下面是她Medium上的連結，她的文章還蠻多有關AI的，寫的也都很好，個人從上面學了很多東西XD</p>
<p>https://medium.com/@chingi071</p>
<p>第三位是巴哈上的別說違心之論好嘛?，下面是他巴哈上的連結，他這篇文章省了我快兩個小時的時間，大感謝</p>
<p>https://home.gamer.com.tw/homeindex.php?owner=aa28131273</p>

  
<p>聯絡方式：lhm0424@gmail.com，有任何疑問或是建議都歡迎聯絡。</p>
<p></p>
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
<p>第三步：點選自己需要的cudnn版本，個人目前使用7.6.5.32版，並根據自己的系統去選擇要下載的檔案點擊下載。</p>
<img src="https://github.com/lhmjimmy/Yolov3-/blob/master/cudnn_version.PNG">
<p>第四步：下載完後解壓縮到自己要的地方，我自己是解壓縮在C槽根目錄下，解壓縮後會得到一個資料夾</p>
<p><img src="https://github.com/lhmjimmy/Yolov3-/blob/master/cudnn_unzip.PNG"></p>
<p>第五步：這邊的操作比較複雜!!!請仔細看 不要因為複雜就跳過喔~這個步驟沒做後面架環境會有問題</p>
<p>這邊的操作比較複雜!!!請仔細看 不要因為複雜就跳過喔~這個步驟沒做後面架環境會有問題</p>
<p>這邊的操作比較複雜!!!請仔細看 不要因為複雜就跳過喔~這個步驟沒做後面架環境會有問題</p>
<p>因為很重要所以說三次!!!</p>

<p>註1：假設版本跟我一樣且都是解壓縮在C槽根目錄下方的話，路徑可以照貼找到檔案，別連檔案名稱都複製貼上喔~複製路徑就好</p>
<p>註2：然後記得是用複製的不要直接把檔案拖拉到另一個資料夾，這樣原始資料夾的檔案會不見，後面遇到檔案找不到的報錯要回到這一步會發現沒有檔案可以用。</p>
<p><h4>1.把 C:\cudnn-10.2-windows10-x64-v7.6.5.32\cuda\bin\cudnn64_7.dll 複製到 C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v10.1\bin中</h4></p>
<p><h4>2.把 C:\cudnn-10.2-windows10-x64-v7.6.5.32\cuda\include\cudnn.h 複製到 C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v10.1\include中</h4></p>
<p><h4>3.把 C:\cudnn-10.2-windows10-x64-v7.6.5.32\cuda\lib\x64\cudnn.lib 複製到 C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v10.1\lib\x64中</h4></p>
<p>cudnn64_7.dll cudnn.h cudnn.lib這三個檔名稍微記一下，後面如果有遇到這三個檔案中其中一個找不到的情況來這邊看一下是否有正確複製到檔案。</p>
<p>
<p><h3>恭喜你~以上步驟都順利完成的話~你的cuda 與cudnn配置就完成囉~</h3></p>
<h2>第二步：安裝Visual Studio</h2>
<p>&emsp;&emsp;個人是裝2019版，之前看到爬文有人推2015跟2017比較不會出錯，不過我用2019除錯了一下也順利的架設好了，所以這邊分享一下Visual Studio2019的安裝方法，如果有大大有更方便的安裝方法歡迎跟我分想一下，之前為了這Visual Studio的部分卡了兩天差點放棄ಥ_ಥ</p>
<p>os:不要用2022，可能後續會更新2022也能用，但是我在用的時候用了半天跟我報錯說此功能限2019以下版本適用我吐了我(／‵Д′)／~ ╧╧</p>
<p>1.：到<a href="https://docs.microsoft.com/zh-tw/visualstudio/releases/2019/release-notes">Visual Studio官網</a>點選Download Community 2019按鈕，個人目前使用2019版，下載完後直接點擊安裝</p>
<p><img src="https://github.com/lhmjimmy/Yolov3-/blob/master/VisualStudio_2019.PNG"></p>
<p>2.：安裝時基本上只要一直下一步就好，直到下方圖片的畫面。勾選1跟2之後，點擊3進行安裝(下方圖是我抓2022的時候截的，不過2019也是同樣的設定，不影響)</p>
<p>註：這邊是選擇要安裝的套件，可以根據自己開發需求選擇要安裝的套件，若不知道安裝什麼就先照著下方圖片勾選，其他套件有需後續都可以繼續安裝</p>
<p><img src="https://github.com/lhmjimmy/Yolov3-/blob/master/VisualStudio_check.PNG"></p>
<h2>第三步：安裝OpenCV</h2>
<p>1.到<a href="https://opencv.org/releases/">OpenCV官網下載要的OpenCV版本</a>，個人目前使用3.4.16</p>
<p>2.下載好後解壓縮到自己要的地方，我是解壓縮在C槽根目錄C:\opencv-3.4.16-vc14_vc15(解壓縮的位置要記得，後面會使用到)</p>
<p>3.然後根據下方圖的步驟，將C:\opencv-3.4.16-vc14_vc15\opencv\build\x64\vc14\bin加入系統Path的環境變數中(路徑需照自己解壓縮的地方設定，不要直接複製)。</p>
<p><img src="https://github.com/lhmjimmy/Yolov3-/blob/master/opencv_envset.png"></p>
<h2>第四步：下載darknet並解壓縮並配置建置環境</h2>
<p>1.到github<a href="https://github.com/AlexeyAB/darknet">下載darknet</a></p>
<p><img src="https://github.com/lhmjimmy/Yolov3-/blob/master/darknet_download.PNG"></p>
<p>2.下載好之後解壓縮到自己要的位置，我是解壓縮在我的G槽G:\darknet-master</p>
<p>3.打開在darknet-master資料夾中的build資料夾，再打開build資料夾中的darknet資料夾，應該會看到如下畫面</p>
<p><img src="https://github.com/lhmjimmy/Yolov3-/blob/master/darknet_cudav.PNG"></p>
<p>4.將上圖中圈起來的檔案拖入你要的編輯器中，我是使用vscode，並修改下列兩處，將CUDA改成自己的版本，例如我的是10.1就改成10.1</p>
<p>註：因為版本的更動行數也許不一定跟我一樣，如果按照圖片上的行數找不到請善用ctrl+F</p>
<p><img src="https://github.com/lhmjimmy/Yolov3-/blob/master/darknet_version1.PNG"></p>
<p><img src="https://github.com/lhmjimmy/Yolov3-/blob/master/darknet_version2.PNG"></p>
<p>5.到C:\Program Files (x86)\MSBuild\Microsoft.Cpp\v4.0\BuildCustomizations確認是否有以下檔案，如果有代表成功了</p>
<p><img src="https://github.com/lhmjimmy/Yolov3-/blob/master/darknet_filecheck.PNG"></p>
如果沒有這些檔案請到C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v10.1\extras\visual_studio_integration\MSBuildExtensions中把裡面的4個檔案copy到C:\Program Files (x86)\MSBuild\Microsoft.Cpp\v4.0\BuildCustomizations中。(路徑通常不會有差異，路徑中通常只會有版本號跟我不一樣v10.1)
<p></p>
<p>6.到3.提到的build資料夾下的darknet資料夾，並用vs2019將darknet.sln開啟，這時應該會看到VisualStudio跳出如下視窗，直接按確認即可</p>
<p><img src="https://github.com/lhmjimmy/Yolov3-/blob/master/VisualStudio_opensln.jpg"></p>
<p>接下來應該會顯示如下畫面，先將畫面中上方的紅框為設定成Release x64。這時下方的紅框會跳出類似下圖中的報錯，這時先不要緊張，有報錯是正常的後面會說如何處理。</p>
<p><img src="https://github.com/lhmjimmy/Yolov3-/blob/master/VisualStuio_openslnerror.jpg"></p>
<p>7.對著右方darknet按右鍵並點擊屬性，如下圖</p>
<p><img src="https://github.com/lhmjimmy/Yolov3-/blob/master/VisualStudio_attributes.jpg"></p>
<p>8.接著依照下圖1234的順序做操作，首先先點選組態屬性中的一般(1.)，在平台工具組右方欄位設定點選下拉式選單的按鈕(2.)，然後選擇Visual Studio(v142)(3.)，然後點選確認(4.)</p>
<p><img src="https://github.com/lhmjimmy/Yolov3-/blob/master/VisualStudio_attributeset.PNG"></p>
<p>9.與7.一樣，對著右方darknet按右鍵並點擊重訂專案目標，如下圖</p>
<p><img src="https://github.com/lhmjimmy/Yolov3-/blob/master/VisualStudio_resetproject.jpg"></p>
<p>點擊後會跑如下視窗</p>
<p><img src="https://github.com/lhmjimmy/Yolov3-/blob/master/VisualStudio_projectresetwindow.jpg"></p>
<p>10.接著Windows SDK 版本選擇一大串數字的，我的是10.0.19041.0(可能會稍有不同不用完全跟我一樣)，然後點擊確定，不要選擇最新安裝的版本</p>
<p><img src="https://github.com/lhmjimmy/Yolov3-/blob/master/VisualStudio_projectresetwindowset.jpg"></p>
<p>點擊完確定後，把VisualStudio關掉後，重新使用VisualStudio開啟darknet.sln，開啟後這時版本問題應該就會不見了，但是會有另一個報錯如下圖</p>
<p><img src="https://github.com/lhmjimmy/Yolov3-/blob/master/VisualStudio_designtimeerro.jpg"></p>
<p>11.這時開啟VisualStudio的cmd(圖中紅框處)</p>
<p><img src="https://github.com/lhmjimmy/Yolov3-/blob/master/VisualStudio_cmd.png"></p>
<p>開啟後輸入以下兩個指令如下圖</p>
<p>set TraceDesignTime=true(此指令是對VisualStudio進行設置，執行後不會顯示任何東西)</p>
<p>devenv(此指令執行結束後會重啟VisualStudio)</p>
<p><img src="https://github.com/lhmjimmy/Yolov3-/blob/master/VisualStudio_cmdrestart.jpg"></p>
<p>12.VisualStudio重啟後一樣用VisualStudio開啟darknet.sln，這時應該會看到如下報錯</p>
<p><img src="https://github.com/lhmjimmy/Yolov3-/blob/master/VisualStudio_temperror.jpg"></p>
<p>打開自己的cmd並輸入%temp%，輸入完之後會看到下面第二章，報錯中的%temp%代表的路徑就是紅圈框起來的路徑(每個人的會根據user名稱而有差異，跟我不一樣是正常的)</p>
<p><img src="https://github.com/lhmjimmy/Yolov3-/blob/master/cmd.png"></p>
<p><img src="https://github.com/lhmjimmy/Yolov3-/blob/master/cmd_temp.jpg"></p>
<p>將上圖紅框中的路徑複製下來，貼到資料夾的路徑中進入報錯中提示的地方，然後按enter，如下圖</p>
<p><img src="https://github.com/lhmjimmy/Yolov3-/blob/master/root.jpg"></p>
<p>接著搜尋designtime，然後按enter，如下圖，這時我們會看到一堆xxxxxxxxxxxxxxxx.designtime.log的檔案</p>
<p><img src="https://github.com/lhmjimmy/Yolov3-/blob/master/root_designtime.jpg"></p>
<p>用記事本隨便開起一個xxxxxxxxxxxxxxxx.designtime.log的檔案，並拉至最下方看看報錯，報錯如下圖紅框，這個報錯簡單的來說就是C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\MSBuild\Microsoft\VC\v160\BuildCustomizations\路徑中沒有CUDA 10.1.props這個檔案。</p>
<p><img src="https://github.com/lhmjimmy/Yolov3-/blob/master/root_designtimeerror.jpg"></p>
<p>這時我們只要將檔案複製到該路徑就好了，方法如下</p>
<p>到C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v10.1\extras\visual_studio_integration\MSBuildExtensions路徑中，將路徑中四個檔案都複製到C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\MSBuild\Microsoft\VC\v160\BuildCustomizations\路徑中即可如下圖</p>
<p><img src="https://github.com/lhmjimmy/Yolov3-/blob/master/root_filecopy.png"></p>
<p>這時關掉VisualStudio後再用VisualStudio開啟darknet.sln應該就不會報錯嚕~</p>
<p>13.接下來就是將opencv加入VisualStudio中~首先與7.一樣對darknet點擊右鍵按屬性並進行以下操作，由於前面有提過了這邊就不截圖了，可以拉回前面看</p>
<p><h3>VC++ 目錄配置</h3></p>
<p><h3>第一步：Include 目錄配置</h3></p>
<p>對Include目錄進行編輯(如圖)</p>
<p><img src="https://github.com/lhmjimmy/Yolov3-/blob/master/VisualStudio_VCset1.PNG"></p>
<p>照圖中提示進行點擊，接著進行下一步</p>
<p><img src="https://github.com/lhmjimmy/Yolov3-/blob/master/VisualStudio_VCset2.PNG"></p>
<p>添加以下三個路徑，如圖(路徑請按自己opencv的位置設定，切勿照貼)，添加完之後按確認</p>
<p>1.C:\opencv-3.4.16-vc14_vc15\opencv\build\include</p>
<p>2.C:\opencv-3.4.16-vc14_vc15\opencv\build\include\opencv</p>
<p>3.C:\opencv-3.4.16-vc14_vc15\opencv\build\include\opencv2</p>
<p><img src="https://github.com/lhmjimmy/Yolov3-/blob/master/VisualStudio_VCset3.PNG"></p>
<p><h3>第二步：程式庫目錄配置</h3></p>
<p>對程式庫目錄進行編輯(如圖)</p>
<p><img src="https://github.com/lhmjimmy/Yolov3-/blob/master/VisualStudio_VCset4.PNG"></p>
<p>照圖中提示進行點擊，接著進行下一步</p>
<p><img src="https://github.com/lhmjimmy/Yolov3-/blob/master/VisualStudio_VCset5.PNG"></p>
<p>將此路徑加入，如圖(路徑請按自己opencv的位置設定，切勿照貼)，添加完之後按確認</p>
<p><img src="https://github.com/lhmjimmy/Yolov3-/blob/master/VisualStudio_VCset6.PNG"></p>
<p><h3>連結器配置</h3></p>
<p><h3>第一步：其他相依性配置如圖</h3></p>
<p><img src="https://github.com/lhmjimmy/Yolov3-/blob/master/VisualStudio_link1.PNG"></p>
<p>將opencv_world3416.lib加入其中(如圖)，添加完之後按確認，下面幾個lib是我自己之前測試加的，跟我不一樣正常，不用擔心</p>
<p>opencv_world3416.lib檔案位於1.C:\opencv-3.4.16-vc14_vc15\opencv\build\x64\vc14\lib 2.C:\opencv-3.4.16-vc14_vc15\opencv\build\x64\vc14\bin這兩個資料夾中。</p>
<p><img src="https://github.com/lhmjimmy/Yolov3-/blob/master/VisualStudio_link2.PNG"></p>
<p><h3>CUDA VC++配置</h3></p>
<p>進入CUDA VC++中，並照下圖點擊操作</p>
<p><img src="https://github.com/lhmjimmy/Yolov3-/blob/master/VisualStudio_Device1.PNG"></p>
<p>將紅框以外的東西都刪掉，然後點擊確認</p>
<p><img src="https://github.com/lhmjimmy/Yolov3-/blob/master/VisualStudio_Device2.PNG"></p>
<h2>第五步：建置darknet</h2>
<p>這一步驟很簡單，只要對darknet按一下右鍵，然後點擊建置就完成了~</p><p>如果前面步驟都有照做順利完成的畫，這個步驟基本上等他跑完就好了，不太會出錯。</p>
<p>註：只要VisualStudio下方資訊欄顯示1成功0失敗就代表成功。</p>
<p>ex:我自己在架的時候曾經遇到過這個報錯，看起來是因為版本衝突或是安裝過多個版本導致的，如果遇到以下報錯的話，把CUDA刪掉照著前面CUDA安裝步驟重裝就好了</p>
<p>報錯：Unexpected compiler version, expected CUDA 10.1 Update 2 or newer.</p>
<h2>第六步：下載Yolo V3權重檔並配置</h2>
<p>1.到下方網址下載Yolov3權重檔</p>
<p>https://pjreddie.com/media/files/yolov3.weights</p>
<p>2.下載好後將yolov3.weights丟入G:\darknet-master\darknet-master\build\darknet\x64中(請將檔案丟入build中的darknet中的x64資料夾，請到自己的路徑中複製路徑下來，不要照貼我的會出錯)</p>
<p><h3>到此配置已經完成嚕~</h3></p>
<h2>測試Yolov3是否能正常運作</h2>
<p>1.打開cmd並進到G:\darknet-master\darknet-master\build\darknet\x64中(請按照自己的路徑，每個人路徑可能會不一樣)</p>
<p>2.輸入如下指令並按enter</p>
<p>darknet detect cfg/yolov3.cfg yolov3.weights data/dog.jpg</p>
<p>接著等他跑一下，如果有順利顯示出這張圖片，就代表建置成功啦~</p>
<p><img src="https://github.com/lhmjimmy/Yolov3-/blob/master/yolo_result.PNG.jpg"></p>
