<h1>
	<font face="Microsoft YaHei" color=green>
		1 SCOPE AND FIELD OF APPLICATION
	</font>
</h1>
<p>
	&nbsp &nbsp Dicom 协议在这部分对Sevice Class Definitions进行了详细说明，Service Class为应用于数字医学信息通讯的现实活动提供了抽象定义。对于每一个Service Class Definitions，这部分协议详细说明了：<br/>
	- Service Class Definition活动的语义描述;<br/>
	- 可以应用于Service Class描述的DIMSE Service操作和通知<font color=red>（被DIMSE传递的数据对象）</font>的组合;</br>
	- 一个或多个功能相关的Service-Object Pair （SOP）Classes，这些SOP Class被Service Class支持并在同级的DICOM Application Entities之间被执行；</br>
	- 每个Service-Object Pair(SOP) Classes与可以应用于这个SOP Class的Information Object Definition(IOD)在PS 3.3中有详细描述。
</p>
<p>
	&nbsp &nbsp与Service Class Definition相关的如下内容，标准在这部分并没有详细说明：</br>
	- 任何关于IOD语义描述的必要信息；</br>
	- Service Class Definition和与IOD相关的现实世界对象的关系；</br>
	- 描述IOD特征的Service Class Definition属性
</p>
<p>
	&nbsp &nbsp与这部分内容相关的DICOM标准的其他部分如下：</br>
	- Part 3, Information Object Definitions, 定义了一套IOD，本部分定义的service可能会被应用到这些IOD上。</br>
	- Part 5, Data Structure and Semantics, 介绍DIMSE协议在应用于本章定义的IOD时使用的数据编码方式；</br>
	- Part 6, Data Dictionary, 包含了本章定义的所有IOD属性标签的索引。这个索引包含了每条属性的VR(Value Representation)和VM(Value Multiplicity)；</br>
	- Part 7, Message Exchange Protocol, 定义了应用于本部分介绍的IOD的DIMSE服务和协议。
</p>