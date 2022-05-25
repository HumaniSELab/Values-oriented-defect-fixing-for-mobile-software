# Detecting values-violating defects in source code (mobile apps)
We are working on building a new taxonomy for mobile app human values, characterising a mobile app model with human values for its target end-users, techniques for detecting values-violating defects in the target mobile apps, and providing recommendations and fixes for these values-violating defects.

A First Look at Human Values-Violation in App Reviews

Ubiquitous technologies such as mobile software applications (mobile apps) have a tremendous influence on the evolution of the social, cultural, economic, and political facets of life in society. Mobile apps fulfil many practical purposes for users including entertainment, transportation, financial management, etc. Given the ubiquity of mobile apps in the lives of individuals and the consequent effect of these technologies on society, it is essential to consider the relationship between human values and the development and deployment of mobile apps. The many negative consequences of violating human values such as privacy, fairness or social justice by technology have been documented in recent times. If we can detect these violations in a timely manner, developers can look to better address them. To understand the violation of human values in a range of common mobile apps, we analysed 22,119 app reviews from Google Play Store using natural language processing techniques. We base our values violation detection approach on a widely accepted model of human values; the Schwartz theory of basic human values. The results of our analysis show that 26.5% of the reviews contained text indicating user perceived violations of human values. We found that benevolence and self-direction were the most violated value categories, and conformity and tradition were the least violated categories. Our results also highlight the need for a proactive approach to the alignment of values amongst stakeholders and the use of app reviews as a valuable additional source for mining values requirements.

Method

To understand the violation of human values in mobile apps, we leverage information contained in users’ apps reviews. App reviews are a valuable source of information, ideas, and requests from users, and we conjecture that app reviews are capable of reflecting human values in mobile apps. Manually analysing feedback from users is a time-consuming process since popular apps typically receive thousands of reviews daily. As a result, automated techniques have been proposed in the literature to reduce the efforts needed for analysing reviews. In this work, we analysed a total of 22,119 app reviews from 12 apps from Google Play Store to identify violations of human values in mobile apps using natural language processing (NLP) techniques. Our approach combines sentiment analysis, app feature extraction, and a human values dictionary of keywords.

Results

Our approach achieves a recall of 0.83, precision of 0.69, and F-measure of 0.75. We base our values detection approach on a widely accepted model of human values, the Schwartz theory of basic human values. The result of our analysis shows that 26.5% of the reviews contained violations of human values. Benevolence and self-direction were the most violated value categories, while conformity and tradition were the least violated value categories. The results also relate certain app features to specific values violation. Furthermore, this study is presented as one of the early steps in understanding the nexus between human values and mobile apps.

Summary

The implications of our results recognise the need for a proactive approach to the elicitation and alignment of human values amongst stakeholders involved in the development of mobile apps to prevent conflicts and values violation. Moreover, app reviews can also serve as a valuable source for mining end user human values requirements to support the evolution of mobile apps via updates and features. We advocate a move towards a critical technical practice in mobile software engineering of employing critical methods and sociocultural reflection of the roles and effects of mobile apps in our society.

Publication

Obie, H., Hussein, W., Xia, X., Grundy, J.C., Li, L., Turhan, B., Whittle, J. and Shahin, M., A First Look at Human Values-Violation in  App Reviews, 2021 IEEE/ACM International Conference on Software Engineering, online 23-29 May 2021, IEEE -- Final publication available atDOI Author pre-published version PDF
Project Lead

Dr Humphrey Obie
Investigators

Prof. John Grundy
Dr Jenny McIntosh
Dr Waqar Hussain
A/Prof. Burak Turhan
Dr Li Li
Prof. Jon Whittle

More information: https://www.monash.edu/it/humanise-lab/projects/living-lab/values-oriented-defect-fixing-for-mobile-software

### Program structure

#### 1. animation

Animation API/hedonism value violation detector

	INPUT:JavaPath java file path
	OUTPUT:return a boolean value:
		True: violation exist
		False: violation does not exist

	/*using deep first search to search all the AST nodes out*/
	AstNodes ← search(JavaPath)
	ViolationList ← an empty list
	VarNames ← an empty list
	for all AstNode in AstNodes do
		if AstNode is Variable Decelerator Nodethen
			if "Animator" inAstN ode.name then
				append AstNode.name to VarNames
			end if
		end if
		if AstNode is Method Invocation Node and AstNode.qualifier in VarNames then
			if AstNode.member ="setDuration" then
				for argument in AstNode.arguements do
					if argument.member > 2000 then
						append "Violation" to ViolationList
					end if
				end for
			end if
			if AstNode.member = "setRepeatCount" then
				for argument in AstNode.arguements do
					if argument.member = "Infinity" then
						append "Violation" in V iolationList
					end if
				end for
			end if
		end if
	end for
	for allListElement in ViolationList do
		if ListElement = "Violation" then
			Return True
		end if
	end for
	Return False





#### 2. hardware

Hardware API/Security value violation detector

	INPUT:JavaP athjava file path
	OUTPUT:return a boolean value:
		True: violation exist
		False: violation does not exist

	/*using deep first search to search all the AST nodes out*/
	AstNodes ← search(JavaPath)
	ViolationList ← an empty list
	VarNames ← an empty list
	for all AstNode in AstNodes do
		if AstNode is VariableDeceleratorNode then
			if "Camera" = AstNode.name and "CameraDevice" = AstNode.namethen
				append AstNode.name to VarNames
			end if
		end if
		if AstNode is MethodInvocationNode and AstNode.qualifier in VarNames then
			if AstNode.member = "takePicture"or AstNode.member = "createCaptureSession" then
				append "Violation" in ViolationList
			end if
		end if
	end for
	for all ListElement in ViolationList do
		if ListElement = "Violation" then
			Return True
		end if
	end for
	Return False



#### 3. media

Media API/Universalism value violation detector

	INPUT:JavaPath java file path
	OUTPUT:return a boolean value:
		True: violation exist
		False: violation does not exist

	/*using deep first search to search all the AST nodes out*/
	AstNodes ← search(JavaPath)
	ViolationList ← an empty list
	VarNames ← an empty list
	
	for all AstNode in AstNodes do
		if AstNode is Import Decelerator Node then
			if "com.google.android.exoplayer"=AstNode.paththen
				append "Violation" in ViolationList
			end if
		end if
	end for

	for all ListElement in ViolationList do
		if ListElement = "Violation" then
			ReturnTrue	
		end if
	end for

	Return False

Media API/self direction and hedonism value violation detector

	INPUT:JavaPath java file path
	OUTPUT:return a boolean value:
		True: violation exist
		False: violation does not exist

	/*using deep first search to search all the AST nodes out*/
	AstNodes ← search(JavaPath)
	/*names of methods which we want to collect about mediaplaying and stop*/
	MethodIdentifyList ← an empty list
	/*names of methods categorized by different object whichwe collected in java file*/
	MethodDict ← an empty dictionary
	VarN ames ← an empty list
	for all AstN ode in AstN odes do
		if AstN ode is Variable Decelerator Node then
			if "MediaPlayer" = AstNode.name then
				append AstNode.nametoVar N ames
			end if
		end if
		if AstNode.member in MethodIdentifyList and AstNode.qualifier in VarNames then 
			append AstNode.member to MethodDict[AstNode.member]
		end if
	end for
	if MethodDict have mediaplay functions but not stop functions for all MediaPlayer objectthen
		Return True
	end if
	Return False



#### 4. mtp

Mtp API/self direction value violation detector

	INPUT:JavaP athjava file path
	OUTPUT:return a boolean value:
		True: violation exist
		False: violation does not exist

	/*using deep first search to search all the AST nodes out*/
	AstNodes ← search(JavaPath)
	/*names of methods which we want to collect about datatransmission*/
	MethodIdentifyList ← an empty list
	/*names of methods which we collected in java file*/
	MethodList ← an empty list
	VarNames ← an empty list
	for all AstNode in AstNodes do
		if AstNode is VariableDeceleratorNode then
			if "MtpDevice" = AstNode.namethen
				append AstNode.nameto VarNames
			end if
		end if
		if AstNode.member in MethodIdentifyList and AstNode.qualifier in VarNames then
			append AstNode.member to MethodList
		end if
	end for
	if MethodList have data transmission function with only one direction then
		Return True
	end if
	Return False


#### 5. nfc

Nfc API/security value violation detector


	INPUT:JavaP athjava file path
	OUTPUT:return a boolean value:
		True: violation exist
		False: violation does not exist

	/*using deep first search to search all the AST nodes out*/
	AstNodes ← search(JavaPath)
	ViolationList ← an empty list
	VarNames ← an empty list
	for all AstNode in AstNodes do
		if AstNode is VariableDeceleratorNode then
			if "Ndef" = AstNode.name then
				append AstNode.name to VarNames
			end if
		end if
		if AstNode is MethodInvocationNode and AstNode.qualifier in VarNames then
			if AstNode.member = "writeNdefMessage" then
				append AstNode.member in MethodInovationList
				if AstNode.member = "createApplicationRecord" then
					append AstNode.member in MethodInovationList
				end if
			end if
		end if
	end for
	if MethodInovationList includes "createApplication-Record" and "writeNdefMessage" then
		Return True
	end if
	Return False


#### 6. telephony

Telephony API/conformity value violation detector

	INPUT:JavaP athjava file path
	OUTPUT:return a boolean value:
		True: violation exist
		False: violation does not exist

	/*using deep first search to search all the AST nodes out*/
	AstNodes ← search(JavaPath)
	ViolationList ← an empty list
	VarNames ← an empty list
	for all AstNode in AstNodes do
		if AstNode is VariableDeceleratorNode then
			if "SmsManager" = AstNode.name then
				append AstNode.name to VarNames
			end if
		end if
		if AstNode is Method Invocation Node and AstNode.qualifier in VarNames then
			if AstNode.member is message sending function name then
				append”Violation”in V iolationList
			end if
		end if
	end for
	for all ListElement in ViolationList do
		if ListElement = "Violation" then
			Return True
		end if
	end for
	Return False


