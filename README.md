# j
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
<title>无标题文档</title>
<script type=" text/javascript">
function demo()
{	
	var divobj = document.getElementById("divid");
   	// divobj.style.backgroundColor="red";
	var name = divobj.nodeName;
	var type =divobj.nodeType;
	var value = divobj.nodeValue;
	alert(name+"..."+type+"..."+value);
	//获取父节点
	//var parent = divobj.parentNode;
	//getNodeInfo(parent);
	//获取子节点
	//var childs = divobj.childNodes;
	//alert(childs.length);
	//getNodeInfo(childs[0]);//获取div中的文本节点
	//获取兄弟节点
		//1、获取上一个兄弟节点
		//var preNode = divobj.previousSibling.previousSibling;	
		//getNodeInfo(preNode);
		//2、获取下一个兄弟节点
		//var nextNode = divobj.nextSibling;
		//getNodeInfo(nextNode);
		//需要a标签的文本
		//var aNode = divobj.nextSibling.nextSibling.nextSibling.nextSibling;
		//var aText = aNode.childNodes;
		//getNodeInfo(aText[0]);
		//需求 获取单元格一文本
		//先获取表格节点
		//
		var tabNode = divobj.nextSibling.nextSibling;
		//getNodeInfo(tabNode.childNodes[1].childNodes[0].childNodes[1]);//太长
		var tdNodes = tabNode.getElementsByTagName("td");
		//getDocAll();
		var nodes = document.all;
		//listNode(nodes);		//getNodeInfo(tdNodes[0].childNodes[0]);
		//var divObj = document.getElementsById("divid");
		//alert(divobj.nodeName);
}

function getNodeInfo(node)
{
	alert(node.nodeName+"类型:"+node.nodeType+"value:" +node.nodeValue+"...");
	
}
var info ="";
function getDocAll()
{
	var nodes = document.all;
	for(var  x = 0; x<nodes.length;x++)
	{
		//getNodeInfo(nodes[x]);	
		info += nodes[x].nodeName+"..."+nodes[x].nodeType+".."+nodes[x].nodeValue+"<br/>";
	}	
//	var node = document.all(7);//可以加索引但是要数节点很麻烦 一般不用
	//getNodeInfo(node);
	document.write(info);
}
/*
public void listFiles(File dir)
{
	System.out.println(getSpace(level)+dir.getNames());
	level++;
	File[] files =dir.listFiles();
	for(int x=0; x<files.length;x++)
	{
		if(files[x].isDirectory)
		 	listFiles(files[x]);
		else
	        System.out.println(getSpace(level)+files[x].getName());	
	}	
}
public String getSpace(int level)
{
	StringBuilder sb = new StringBuilder();
	for(int x=0;x<level;x++)
	{
		sb.append(" ");
		
	}	
	return sb.toString();
}

*/
//通过递归获取节点的层次关系
var str= "";
function listNode(node,level)
{
	printInfo(node,level);
	level++;
	var nodes = node.childNodes;
	for(var x=0;x<nodes.length;x++)
	{
		if(nodes[x].hasChildNodes())
			listNode(nodes[x],level);
		else
			printInfo(nodes[x],level);	
	}	
}
function getSpace(level)
{
		var s ="";
		for(var x= 0;x<level;x++)
		{
			s +="|--";	
		}
		return s;
		
}
function printInfo(node,level)
{
	
	str += getSpace(level)+node.nodeName+"类型:"+node.nodeType+"value:" +node.nodeValue+"..."+"<br/>";
	
}
function getNodes()
{
	listNode(document,0);	
	document.write(str);
}
function getAtts()//属性节点
{
	var q="";
	var divObj = document.getElementById("table");
	
	var atts = divObj.attributes;
	//alert(atts.length);
	for(var x=0; x<atts.length;x++)
	{
		q += atts[x].nodeName+".."+atts[x].nodeType+".." +atts[x].nodeValue+"...";
	}	
	document.write(q); 
}

</script>
</head>

<body>
<input type="button" value="演示" onclick="getAtts()" />
<input type="button" value="demo" onclick="demo()" />
<script type="text/javascript">
/*var x= 5;
alert(x.toString(2));*/
</script>
<div id="divid">
dsadsa
</div>

<table id="table">
    <tr>
        <td>单元格一</td>
        <td>单元格二</td>
    </tr>
    <tr>
        <td>单元格三</td>
        <td>单元格四</td>
    </tr>
</table>
<a href="http://www.baidu.com">百度</a>
<span>span区域</span>
</body>
</html>
