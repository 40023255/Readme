@cherrypy.expose
# N 為齒數, M 為模數, P 為壓力角
def do3Dgear(self, N=20, M=5, P=15):
    outstring = '''
<!DOCTYPE html> 
<html>
<head>
<meta http-equiv="content-type" content="text/html;charset=utf-8">
<!-- 載入 brython.js -->
<script type="text/javascript" src="/static/Brython3.1.1-20150328-091302/brython.js"></script>
<script src="/static/Cango2D.js" type="text/javascript"></script>
<script src="/static/gearUtils-04.js" type="text/javascript"></script>
</head>
<!-- 啟動 brython() -->
<body onload="brython()">
<!-- 以下為 canvas 畫圖程式 -->
<script type="text/python">
# 從 browser 導入 document
from browser import document
import math

# 畫布指定在名稱為 plotarea 的 canvas 上
canvas = document["plotarea"]
ctx = canvas.getContext("2d")

# 用紅色畫一條直線
ctx.beginPath()
ctx.lineWidth = 3
'''
    outstring += '''
ctx.moveTo('''+str(N)+","+str(M)+")"
    outstring += '''
ctx.lineTo(0, 500)
ctx.strokeStyle = "red"
ctx.stroke()

# 用藍色再畫一條直線
ctx.beginPath()
ctx.lineWidth = 3
ctx.moveTo(0, 0)
ctx.lineTo(500, 0)
ctx.strokeStyle = "blue"
ctx.stroke()

# 用綠色再畫一條直線
ctx.beginPath()
ctx.lineWidth = 3
ctx.moveTo(0, 0)
ctx.lineTo(500, 500)
ctx.strokeStyle = "green"
ctx.stroke()

# 用黑色畫一個圓
ctx.beginPath()
ctx.lineWidth = 3
ctx.strokeStyle = "black"
ctx.arc(250,250,50,0,2*math.pi)
ctx.stroke()
</script>
<canvas id="plotarea" width="800" height="600"></canvas>
</body>
</html>
'''

    return outstring
