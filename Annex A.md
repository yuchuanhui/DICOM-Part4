<h1>
	<font face="Microsoft YaHei" color=green>
		Annex A	VERIFICATION SERVICE CLASS (Normative)
	</font>
</h1>
<h2>
	A.1	OVERVIEW
</h2>
<h3>
	A.1.1 Scope
</h3>
<p>
	&nbsp &nbsp 验证服务类定义了同级DICOM AE之间交互验证。验证是在连接建立时使用C-ECHO DIMSE-C服务完成的。
</p>
<h2>
	A.2	SCU/SCP BEHAVIOR
</h2>
<p>
	&nbsp &nbsp 支持验SOP Class中SCU角色的DICOM AE会向远端的DICOM AE发送交互验证请求。请求是用C-ECHO请求原语执行的。远端支持验证SOP Class中SCP角色的DICOM AE会发送一个C-ECHO应答原语。SCU通过接收C-ECHO确认来判断是否完成。C-ECHO原语的相关规定参见PS 3.7。
</p>
<h2>
	A.3	DIMSE-C SERVICE GROUP
</h2>
<p>
	&nbsp &nbsp C-ECHO DIMSE-C 服务被用于同级DICOM AE之间交互验证的机制。C-ECHO服务和协议的参数要满足PS3.7中的定义。
</p>