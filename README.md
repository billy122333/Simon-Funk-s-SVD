# Simon-Funk-s-SVD

## SVD是什么

  SVD，奇異值分解，是一種矩陣分解的方法，SVD可用於特徵提取或矩陣降维。降维不是簡單的維度縮小，而是維度變小後，矩陣的原始信息没有很大的改變。

## SVD如何使用到推薦系统

在這里，我們使用的思想和降維的出發點不一樣，我們使用的是SVD可以進行“矩陣分解”這一特點。我們在召回階段的目的是由一個稀疏的評分矩陣推算出其中的空缺分數。

我們的目的是得到用戶對未評價電影的分數，而這種user-Item的評分矩陣中，用戶對Item的分數是沒有直接關系的，我們需要尋找一種隱空間，使得將用戶和Item聯系起來。比如我們無法得知user1對《利刃出鞘》這部電影的分數，但是我們可以通過用戶的歷史信息（即用戶對別的電影的分數）得到用戶對“懸疑”類電影的愛好程度，我們也可以得到某個電影的“懸疑類”的程度有多大，這樣，我們就可以將這倆個關系聯系到一起了，比如我們想用戶A對《南方車站的故事》進行預測，我們無法直接得到他的分數，但是我們知道他對“懸疑”類的電影有多喜愛，而《南方車站的故事》的“懸疑”程度有多大，兩個值相乘即可得到A對《南方車站的故事》的預測分數，這里我們只是使用到了一個維度：“懸疑”類，我們可以將矩陣A分解成m* k列的一共k個維度的矩陣，將電影分解成k * n列一共k個維度的矩陣，然後這兩個矩陣相乘即可得到矩陣中空的A[i][j]的值。

說白了，我們這里使用到得SVD的思想只是說任何一個矩陣均可以分解成兩個矩陣相乘的形式（SVD是三個，但也可以合並倆個得到兩個矩陣），這倆個子矩陣分別代表了用戶的偏好程度和電影的成分程度，將這兩個矩陣相乘即可得到用戶對電影的評分矩陣。

## Result
P X Q 產出的 評分預測值

![P X Q 產出的 評分預測值](https://user-images.githubusercontent.com/75492436/220559732-40dbd544-5e37-4e6f-b285-26450c893939.png)
