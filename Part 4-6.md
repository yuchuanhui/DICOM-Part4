<h1>
	<font face="Microsoft YaHei" color=green>
		6 DICOM INFORMATION MODEL
	</font>
</h1>
<p>
	&nbsp &nbsp DICOM信息模型定义了医学影像传输相关的组织和结构。图6-1展示了DICOM信息模型主要结构之间的关系。
</p>
<h2>
	6.1	INFORMATION OBJECT DEFINITION
</h2>
<p>
	&nbsp &nbsp信息对象定义（IOD）是一个面向对象的抽象数据模型，用来描述现实世界对象的信息。IOD为交互的应用实体（AE）提供了共同的信息交换模型
</p>
<p>
	&nbsp &nbsp IOD并不是描述现实世界中某个对象实例，而是描述了一类具有相同属性的对象。描述现实世界中单一类型的IOD被称为标准信息对象。包含了现实世界中相关对象信息的IOD被称为复合信息对象。
</p>
<h3>
	6.1.1	Composite IOD
</h3>
<p>
	&nbsp &nbsp复合IOD是描述部分DICOM现实世界模型的实例的信息对象（参见PS3.3）。这类IOD包含一些不属于IOD描述现实世界对象而属于与其相关的对象的属性。
	<font size = 2 color = red>
		&nbsp &nbsp（就是说只有在几个相关对象共同出现时才有的属性）
	</font>。
</p>
<p>
	&nbsp &nbsp这些相关的现实世界对象为信息交互提供了完整的上下文背景。当一个复合IOD实例被用来做信息交互时，整个上下文背景都会在应用实例（AE）间进行传递。复合IOD实例间的关系是在这个上下文背景信息中传递的。</br>
	<font size = 2>
		&nbsp &nbsp注意： 1.实际的IOD实例间的交互是通过SOP Instance完成的。</br>
		&nbsp &nbsp &nbsp &nbsp  &nbsp &nbsp &nbsp 2.在复合IOD实例的实际关联中，一些背景信息是冗余的（也就是说相同的现实世界对象信息可能被包含在多个SOP Instance中）。
	</font></br>
	&nbsp &nbsp复合IOD的具体说明参见PS3.3。
</p>
<h3>
	6.1.2 Normalized IOD
</h3>
<p>
	&nbsp &nbsp标准IOD一般是描述单一的DICOM现实世界模型实例的信息对象模型。</br>
	&nbsp &nbsp当一个标准IOD实例被传递时，它的上下文实际上并没有被传递。上下文背景是通过对相关标准IOD实例指针的使用提供的。</br>
	&nbsp &nbsp标准IOD的具体说明参见PS3.3。
</p>
<h2>
	6.2	ATTRIBUTES
</h2>
<p>
	&nbsp &nbsp IOD的属性描述了现实世界对象实例的特性。相关的属性被分组到不同的模块中，模块是一种高级语义，可以在PS3.3中找到模块的定义。</br>
	&nbsp &nbsp属性使用数据元素按照一定规则进行编码，值描述（VR）和值多重性（VM）在PS3.5中说明。不同数据元素的值描述（VR）和值多重性（VM）在PS3.6——数据字典中描述。
</p>
<h2>
	6.3	ON-LINE COMMUNICATION AND MEDIA STORAGE SERVICES
</h2>
<p>
	&nbsp &nbsp对于在线通讯，DIMSE服务允许应用实例通过网络操作和发送通知，或者调用点对点的接口。DIMSE服务在PS3.7中定义。</br>
	&nbsp &nbsp对于与存储介质交互，存储介质服务允许DICOM应用实例调用与存储介质相关的操作。</br>
	&nbsp &nbsp存储介质服务在PS3.10中讨论。
</p>
<h3>
	6.3.1 DIMSE-C Services
</h3>
<p>
	&nbsp&nbsp DIMSE-C服务只能应用于复合IOD。DIMSE-C服务只提供操作服务。
</p>
<h3>
	6.3.2 DIMSE-N Services
</h3>
<p>
	&nbsp&nbsp DIMSE-N服务只能应用于标准IOD。DIMSE-N服务既提供服务也提供通知。
</p>
<h2>
	6.4	DIMSE SERVICE GROUP
</h2>
<p>
	&nbsp&nbsp DIMSE服务组描述了一个或多个应用于一个IOD的操作/通知，这些操作/通知在PS3.7中定义。</br>
	&nbsp&nbsp DIMSE在DICOM标准的这部分中被定义，用来描述一个服务-对象组类型（Service Object Pair Class）。
</p>
<h2>
	6.5	SERVICE-OBJECT PAIR (SOP) CLASS
</h2>
<p>
	&nbsp&nbsp服务-对象组类型是IOD和DIMSE服务组的组合。SOP类型的定义包括一些规则和语义，它们限定了对DIMSE服务组中的服务和IOD中的属性的使用方式。</br>
	&nbsp&nbsp应用实例通过选择SOP类型，并保证各自具有该类型中协义好的功能，从而完成交互。就像PS3.7中描述的那样，这些协议在建立链接时被执行。扩展的协议允许应用实例在某一个IOD特有的选项上进行进一步规定。</br>
	<font size = 2>
		&nbsp&nbsp注意：在DICOM信息模型中定义的SOP类型与ISO/OSI中的术语——管理对象类型（Managed Object Class）相似。熟悉面向对象术语的读者会发现SOP类型操作（或通知）就是一个对象类型的方法。
	</font>
</p>
<h3>
	6.5.1 Normalized and Composite SOP Classes
</h3>
<p>
	&nbsp&nbsp DICOM定义了两种类型的SOP类型，标准的和复合的。标准SOP类型被定义为标准IOD和一组DIMSE-N服务的组合。复合SOP类型定义为复合IOD和一组DIMSE-C服务的组合。</br>
	<font size = 2>
		&nbsp&nbsp SOP类型的说明是DICOM一致性定义的核心。SOP类型允许DICOM应用实例选择协议中定义好的一个应用层子集来声明它们之间的一致性。
	</font>
</p>
<h2>
	6.6	ASSOCIATION NEGOTIATION
</h2>
<p>
	&nbsp&nbsp建立连接是两个符合DICOM标准的同级应用实例进行交互的第一阶段。应用实例在连接建立阶段约定好协议，哪些SOP类型可以被传递，对应数据该如何编码。</br>
	&nbsp&nbsp连接协议在PS3.7中定义。
</p>
<h2>
	6.7	SERVICE CLASS SPECIFICATION
</h2>
<p>
	&nbsp&nbsp一个服务类型规范定义了一组与特定功能相关的SOP类型，这些功能是通过应用实例交互完成的。服务类型规范还定义了一套规则，允许具体实现以预先设定的等级说明其对一个或多个SOP类型的符合程度。应用既可以以服务类型使用者（SCU）也可以服务类型提供者（SCP）的角色符合SOP类型。</br>
	&nbsp&nbsp SOP类型规范在协议的这部分被定义。</br>
	<font size = 2>
		&nbsp&nbsp注意：这种同级应用实例间的交互采用了“客户端/服务端”模型。SCU作为客户端，而SCP作为服务端。SCU/SCP的角色是在连接建立时决定的。
	</font>
</p>