#install.packages("VennDiagram")
library(VennDiagram)
data#自己的数据
otus =rownames(data)
sets =colnames(data)
option ="MO-MU-SJ-SA"#分类名，指定比较组，以"_"分隔
newgroup =unlist(strsplit(option,"-"))#获取指定的新分组名称
x =list()
x[["CESC"]]=rownames(CESC_HPV)
x[["UCEC"]]=rownames(UCEC_HPV)#举例
str(x)#查看列表x的结构；
Chevalier1<-c("#355243","#fbca50","#c9d5d4","#baa28a") #载入个人收藏的wesanderson包颜色列表
FantasticFox1<-c("#d37a20","#dbcb09","#3a9cbc","#dd7208","#a30019")
Moonrise3<-c("#75cbdc","#f0a4af","#8a863a","#c2b479","#f8d068")
Cavalcanti1<-c("#ceab0d","#083215","#919562","#6f997a","#831e11")
Darjeeling2<-c("#e6c09e","#0d5888","#cb8b3e","#9cd6d6","#000000")
Darjeeling1<-c("#fb0007","#139177","#ed9e08","#f56f08","#4caecc")
Royal2<-c("#e4c9b2","#f1c2a5","#f49d98","#fcd68f","#629076")
IsleofDogs2<-c("#e4c9b2","#998273","#a6723d","#2b2523","#151213")
color_list = Darjeeling1#选择一个颜色列表
fill_colors = color_list[1:length(x)]#依照指定的新分组数选取颜色列
VENN<-venn.diagram(x,col="white",fill=fill_colors,
                   scaled=F,#不自动缩放
                   lwd=0.5,#轮廓宽度
                   filename=NULL,#不保存
                   cex=2,#数字大小
                   cat.cex=2,#标签大小
                   width=1200,height=1200)
pdf("./Dicussion/venn/VENN.pdf")
grid.draw(VENN)
dev.off()

