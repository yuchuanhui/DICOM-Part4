<h1>
	<font face="Microsoft YaHei" color=green>
		5 CONVENTIONS
	</font>
</h1>
<h2>
	5.1 ENTITY-RELATIONSHIP MODEL
</h2>
<h3>
	5.1.1 Entity
</h3>
<p>
	&nbsp &nbsp 实体在实体关系(E-R)模型中被用来代表现实世界中的对象，现实世界中对象的类型，或者DICOM数据描述，例如IOD或模块（Module）等。在DICOM协议的这部分中，实体被用一个方形表示，如图5-1所示：
</p>
<h3>
	5.1.2 Relationship
</h3>
<p>
	&nbsp &nbsp 关系定义了实体之间是如何被联系起来的，在协议中用菱形表示，如图5-2所示。
</p>
<p>
	&nbsp &nbsp 关系表示了从源实体到目标实体的关联，如图中箭头所示的那样。箭头a和b分别表示了源集合和目标集合的“势”。“势”的类型如下：</br>
	a. (a = 1, b = 1)——一个源实体与一个目标实体相关联；</br>
	b. (a = 1, b = 0-n)——一个源实体与0或多个目标实体相关联；</br>
	c. (a = 1, b = 1-n)——一个源实体与一个或多个目标实体相关联；</br>
	d. (a = 1-n, b = 1)——一个或多个源实体与一个目标实体相关联；</br>
	e. (a = 1-n, b = 0-n)——一个或多个源实体与0或多个目标实体相关联；</br>
	f. (a = 1-n, b = 1-n)——一个或多个源实体与一个或多个目标实体相关联。</br>
在一个(a = 1-n, b = 1-n)的关系中，源集合和目标集合的“势”的值可能是不同的。n仅仅表示1或者更多。</br></br>
	<font size = 2>
		&nbsp &nbsp 注意：DICOM与其他地方使用的E-R图有所不同，给无向边加了箭头，从而避免因顺序被弄反而造成对关系理解的错误，例如，在没有箭头的情况下，“猫捉老鼠”的关系可能会被理解为“老鼠捉猫”的关系。
	</font></br></br>
	有些关系可能是双向的（也就是说两个方向的关系都是正确的）。DICOM协议规定，这种情况，箭头既指向源实体又指向目标实体。
</p>
<h2>
	5.2	SEQUENCES
</h2>
<p>
	&nbsp &nbsp 在DICOM协议的这部分的某些表格中，用符号“>”表示一个条目序列。</br>
	&nbsp &nbsp 在附录A中，“>”代表一个模块序列，嵌套的模块序列中符号“>>”表示。在附录B和C中，“>”表示一个属性序列。条目序列如何编码的完整说明参见PS3.5。</br>
	<font size = 2>
		&nbsp &nbsp 注意：包含模块序列的信息对象定义（IOD）经常被称作文件。但是属性序列的使用不仅仅限于文件。
	</font>
</p>
<h2>
	5.3 RESPONSE STATUS VALUES
</h2>
<p>
	&nbsp &nbsp 在这部分DICOM协议的某些表格中，标识了一些与具体实现相关的应答状态代码，并用'xx' 符号代表代码的一部分。
</p>
<h2>
	5.4 USAGE SPECIFICATION
</h2>
<p>
	&nbsp &nbsp 构建SOP Classes的基本单元是模块（Modules）和DIMSE服务。与一个SOP Class相关的DIMSE服务可能是强制（M）的，也可能是可选（U）的。DIMSE服务的使用对于SCU与SCP可能是不同的。使用方式用一对字母进行说明，前者表示标识SCU的DIMSE服务使用，后者标识SCP的DIMSE使用。
</p>
<p>
	&nbsp &nbsp下面具体描述DIMSE服务使用规范的意义和行为：</br> 
	&nbsp &nbsp M/M SCU需要支持DIMSE服务，但并不用必须在SCU与SCP连接时使用。SCP需要是支持DIMSE服务。</br>
	&nbsp &nbsp U/M SCU对于DIMSE服务的支持和使用时可选的，SCP需要支持DIMSE服务。</br>
	&nbsp &nbsp U/U SCU对于DIMSE服务的支持和使用时可选的，SCP对DIMSE服务的支持和使用也是可选的。如果SCP不支持SCU使用的DIMSE服务，SCP需要返回一个失败状态。
</p>
<p>
	&nbsp &nbsp 模块及其在复合IOD中的使用时在PS3.3中定义的。标准IOD也是由模块构成的，但是阐述对它们的使用是基于这部分协议中定义的属性基础。除非被某个SOP Class的使用规范禁止，否则下面的使用规范会应用于标准IOD的所有属性。
</p>
<p>
	&nbsp &nbsp 标准IOD属性使用规范的意义和行为如下：</br>
	&nbsp &nbsp 1/1——SCU负责为属性提供一个值。如果SCU不提供这个值，那么SCP应该返回失败状态代码（"缺少属性" 代码0120H）。SCP负责提供这个属性。SCP不允许属性值为空（不给属性提供值且值的长度为0）。</br>
	&nbsp &nbsp 3/1——SCU可能检索这个属性的值或者给属性赋值。SCP需要支持这个属性。SCP不允许属性值为空（不给属性提供值且值的长度为0）。</br>
 	&nbsp &nbsp -/1——SCU对属性的使用时未定义的。SCP需要支持这个属性。SCP不允许属性值为空（不给属性提供值且提供的值长度为0）。</br>
	&nbsp &nbsp 2/2——SCU必须检索这个属性或给这个属性赋值。SCU应该总是提供这个属性，但是值允许为空（不给属性提供值且值的长度为0）。SCP必须支持这个属性，但是属性值允许为空（不给属性提供值且值的长度为0）</br>
	&nbsp &nbsp 3/2——SCU可能检索这个属性或给属性赋值。SCP需要支持这个属性，并且允许属性值为空（不给属性提供值且值的长度为0）。</br>
	&nbsp &nbsp -/2——SCU对属性的使用时未定义的。SCP需要支持这个属性，并且允许属性值为空（不给属性提供值且值的长度为0）。</br>
	&nbsp &nbsp 3/3——SCU可能检索这个属性的值或者给属性赋值。SCP可能支持这个属性。如果SCP不支持这个属性，SCU向其发送了关于这个属性的请求，SCP应该返回一个失败状态（“无效属性”,代码0106H），或者一个警告状态（“属性值超出范围”, 代码0116H）。如果SCU提供了一个属性，SCP不支持这个属性，并且返回失败或者警告,那么属性应该被忽略。
</p>
<p>
	&nbsp &nbsp 如果SCP应用类型名称后面附件一个“C”（例如，3/1C），那么上述描述的规范就应该对应修改为在某条件满足时，SCP应该支持这些属性。
</p>
<p>
	&nbsp &nbsp 对于所有N-CREATE, N-SET, N-GET, N-DELETE, N-ACTION和N-EVENT-REPORT操作， SOP Class是在Affected SOP Class UID(0000,0002)的请求原语中传递的，因此SOP Class UID(0008,0016)属性不应该出现在数据集中。
</p>
<p>
	&nbsp &nbsp 对于N-CREATE操作和N-EVENT-REPORT通知，SOP Instance是通过Affected SOP Instance UID (0000,1000)传递的。因此SOP Instance UID (0008,0018)不应该出现在数据集中。
</p>
<p>
	<font size = 2>
		&nbsp &nbsp 注意：在一些Service Class中，SOP Class的定义可能会被PS3.7中的通用条款覆盖，这些条款允许SOP instance UID被N-CREATE的请求原语指定或删除，并且要求SCU负责指定SOP Instance UID。
	</font>
</p>
<p>
	&nbsp &nbsp 在N-SET, N-GET, N-ACTION和N-DELETE操作中，SOP Instance是通过Requested SOP Instance UID (0000,1001)传递的。因此SOP Instance UID (0008,0018)不应该出现在数据集中。
</p>
