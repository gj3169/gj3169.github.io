---
title: 一个matlab GUI使用例子，pop-up menu的用法
author: gj3169
layout: post
permalink: /2015/04/yigematlabguishiyonglizipop-upmenudeyongfa/
views:
  - 14
bluet_exclude_post_from_matching:
  - 
bluet_matching_keywords_field:
  - 'a:0:{}'
tc-thumb-fld:
  - 'a:2:{s:9:"_thumb_id";i:22;s:11:"_thumb_type";s:10:"attachment";}'
post_stats:
  - 5
categories:
  - coding
tags:
  - GUI
  - matlab
  - popup
---
本例子要实现的GUI功能是这样的，从一个EXCEL文件中读取数据，并将数据分类，作图的算例。数据按照下图中的H\_aem和av\_scr的不同数据进行分类。

<div>
</div>

<div>
  EXCEL中的内容大概是这样的如下图所示，共有1000多行。手动解决确实比较费力。
</div>

<div>
</div>

<div>
  <a href="http://7xind4.com1.z0.glb.clouddn.com/uploads/2015/04/001A4kBWzy6NWG6cVFwb2.png"><br /> </a><a href="http://7xind4.com1.z0.glb.clouddn.com/uploads/2015/04/001A4kBWzy6NWG6cVFwb2.png"><img class="alignnone size-medium wp-image-22" src="http://7xind4.com1.z0.glb.clouddn.com/uploads/2015/04/001A4kBWzy6NWG6cVFwb2-300x235.png" alt="001A4kBWzy6NWG6cVFwb2" width="300" height="235" /></a>
</div>

<div>
</div>

<div>
  <span style="color: #ff0000;">一个简单的matlab 的gui程序包含两个文件，一个是.fig文件，一个是.m文件，两个文件是有相同的名字的。</span>首先来看.fig文件如何建立。
</div>

<div>
  下面打开matlab的guide，命令行直接键入guide回车就好
</div>

<div>
  <a href="http://7xind4.com1.z0.glb.clouddn.com/uploads/2015/04/001A4kBWzy6NWGq4RmJ95690.jpg"><img class="alignnone size-medium wp-image-21" src="http://7xind4.com1.z0.glb.clouddn.com/uploads/2015/04/001A4kBWzy6NWGq4RmJ95690-300x163.jpg" alt="001A4kBWzy6NWGq4RmJ95&690" width="300" height="163" /></a>
</div>

<div>
</div>

<div>
  选择default就好，点击OK。
</div>

<div>
  <a href="http://7xind4.com1.z0.glb.clouddn.com/uploads/2015/04/001A4kBWzy6NWGvx75N2b690.png"><img class="alignnone size-medium wp-image-20" src="http://7xind4.com1.z0.glb.clouddn.com/uploads/2015/04/001A4kBWzy6NWGvx75N2b690-300x194.png" alt="001A4kBWzy6NWGvx75N2b&690" width="300" height="194" /></a>
</div>

<div>
</div>

<div>
</div>

<div>
</div>

<div>
  如下图所示，将各个部件添加进去
</div>

<div>
  <a href="http://7xind4.com1.z0.glb.clouddn.com/uploads/2015/04/001A4kBWzy6NWGKpqXta7690.png"><img class="alignnone size-medium wp-image-19" src="http://7xind4.com1.z0.glb.clouddn.com/uploads/2015/04/001A4kBWzy6NWGKpqXta7690-300x256.png" alt="001A4kBWzy6NWGKpqXta7&690" width="300" height="256" /></a>
</div>

<div>
</div>

<div>
</div>

<div>
  做好后就是下图这个效果
</div>

<div>
  <a href="http://7xind4.com1.z0.glb.clouddn.com/uploads/2015/04/001A4kBWzy6NWGW5PaA94690.jpg"><img class="alignnone size-medium wp-image-17" src="http://7xind4.com1.z0.glb.clouddn.com/uploads/2015/04/001A4kBWzy6NWGW5PaA94690-300x165.jpg" alt="001A4kBWzy6NWGW5PaA94&690" width="300" height="165" /></a>
</div>

<div>
  稍微有点丑，各位可以自己美化一下哈
</div>

<div>
</div>

<div>
  Pop-up Menu双击后出现的对话框中的string项要设置好，需要用户有哪几种选择。
</div>

<div>
</div>

<div>
</div>

<div>
  下一步就是最重要的一步，给各个按钮神马的编写code
</div>

<div>
  由于按钮较多，本文主要写一下Pop-up Menu的Callback编写方法
</div>

<div>
  代码如下，str{val}就可以得到当选择了某个项时，得到的字符串是什么。用的switch结构。
</div>

<div>
  <div>
    str = get(hObject, &#8216;String&#8217;);
  </div>
  
  <div>
    val = get(hObject,&#8217;Value&#8217;);
  </div>
  
  <div>
    % Set current data to the selected data set.
  </div>
  
  <div>
    switch str{val};
  </div>
  
  <div>
    case &#8216;1e-6&#8217;
  </div>
  
  <div>
       handles.H_aem = 1e-6;
  </div>
  
  <div>
    case &#8216;3e-6&#8217;
  </div>
  
  <div>
       handles.H_aem = 3e-6;
  </div>
  
  <div>
    case &#8216;5e-6&#8217;
  </div>
  
  <div>
       handles.H_aem = 5e-6;
  </div>
  
  <div>
    case &#8216;7e-6&#8217;
  </div>
  
  <div>
       handles.H_aem = 7e-6;
  </div>
  
  <div>
    case &#8216;9e-6&#8217;
  </div>
  
  <div>
       handles.H_aem = 9e-6;
  </div>
  
  <div>
    end
  </div>
  
  <div>
    guidata(hObject,handles)%这一句非常重要，如果没有这一句，句柄handles.H_aem是无法更新的
  </div>
</div>

<div>
</div>

<div>
</div>

<div>
  <span style="color: #ff0000;">附上m文件的全文</span></p> 
  
  <div>
    function varargout = H_aem_av(varargin)
  </div>
  
  <div>
    %H_AEM_AV M-file for H_aem_av.fig
  </div>
  
  <div>
    %      H_AEM_AV, by itself, creates a new H_AEM_AV or raises the existing
  </div>
  
  <div>
    %      singleton*.
  </div>
  
  <div>
    %
  </div>
  
  <div>
    %      H = H_AEM_AV returns the handle to a new H_AEM_AV or the handle to
  </div>
  
  <div>
    %      the existing singleton*.
  </div>
  
  <div>
    %
  </div>
  
  <div>
    %      H_AEM_AV(&#8216;Property&#8217;,&#8217;Value&#8217;,&#8230;) creates a new H_AEM_AV using the
  </div>
  
  <div>
    %      given property value pairs. Unrecognized properties are passed via
  </div>
  
  <div>
    %      varargin to H_aem_av_OpeningFcn.  This calling syntax produces a
  </div>
  
  <div>
    %      warning when there is an existing singleton*.
  </div>
  
  <div>
    %
  </div>
  
  <div>
    %      H_AEM_AV(&#8216;CALLBACK&#8217;) and H_AEM_AV(&#8216;CALLBACK&#8217;,hObject,&#8230;) call the
  </div>
  
  <div>
    %      local function named CALLBACK in H_AEM_AV.M with the given input
  </div>
  
  <div>
    %      arguments.
  </div>
  
  <div>
    %
  </div>
  
  <div>
    %      *See GUI Options on GUIDE&#8217;s Tools menu.  Choose &#8220;GUI allows only one
  </div>
  
  <div>
    %      instance to run (singleton)&#8221;.
  </div>
  
  <div>
    %
  </div>
  
  <div>
    % See also: GUIDE, GUIDATA, GUIHANDLES
  </div>
  
  <div>
  </div>
  
  <div>
    % Edit the above text to modify the response to help H_aem_av
  </div>
  
  <div>
  </div>
  
  <div>
    % Last Modified by GUIDE v2.5 27-Nov-2014 21:22:17
  </div>
  
  <div>
  </div>
  
  <div>
    % Begin initialization code &#8211; DO NOT EDIT
  </div>
  
  <div>
    gui_Singleton = 1;
  </div>
  
  <div>
    gui_State = struct(&#8216;gui_Name&#8217;,       mfilename, &#8230;
  </div>
  
  <div>
                       &#8216;gui_Singleton&#8217;,  gui_Singleton, &#8230;
  </div>
  
  <div>
                       &#8216;gui_OpeningFcn&#8217;, @H_aem_av_OpeningFcn, &#8230;
  </div>
  
  <div>
                       &#8216;gui_OutputFcn&#8217;,  @H_aem_av_OutputFcn, &#8230;
  </div>
  
  <div>
                       &#8216;gui_LayoutFcn&#8217;,  [], &#8230;
  </div>
  
  <div>
                       &#8216;gui_Callback&#8217;,   []);
  </div>
  
  <div>
    if nargin && ischar(varargin{1})
  </div>
  
  <div>
       gui_State.gui_Callback = str2func(varargin{1});
  </div>
  
  <div>
    end
  </div>
  
  <div>
  </div>
  
  <div>
    if nargout
  </div>
  
  <div>
        [varargout{1:nargout}] = gui_mainfcn(gui_State, varargin{:});
  </div>
  
  <div>
    else
  </div>
  
  <div>
        gui_mainfcn(gui_State, varargin{:});
  </div>
  
  <div>
    end
  </div>
  
  <div>
    % End initialization code &#8211; DO NOT EDIT
  </div>
  
  <div>
  </div>
  
  <div>
  </div>
  
  <div>
    % &#8212; Executes just before H_aem_av is made visible.
  </div>
  
  <div>
    function H_aem_av_OpeningFcn(hObject, eventdata, handles, varargin)
  </div>
  
  <div>
    % This function has no output args, see OutputFcn.
  </div>
  
  <div>
    % hObject    handle to figure
  </div>
  
  <div>
    % eventdata  reserved &#8211; to be defined in a future version of MATLAB
  </div>
  
  <div>
    % handles    structure with handles and user data (see GUIDATA)
  </div>
  
  <div>
    % varargin   unrecognized PropertyName/PropertyValue pairs from the
  </div>
  
  <div>
    %            command line (see VARARGIN)
  </div>
  
  <div>
  </div>
  
  <div>
    % Choose default command line output for H_aem_av
  </div>
  
  <div>
    handles.output = hObject;
  </div>
  
  <div>
  </div>
  
  <div>
    % Update handles structure
  </div>
  
  <div>
    guidata(hObject, handles);
  </div>
  
  <div>
    handles.H_aem=1e-6;
  </div>
  
  <div>
    guidata(hObject,handles)
  </div>
  
  <div>
    handles.av=1e6;
  </div>
  
  <div>
    guidata(hObject,handles)
  </div>
  
  <div>
    [handles.num,handles.txt] = xlsread(&#8216;C:UsersJianDocumentsMATLABH_aem-av_scr.xls&#8217;,&#8217;H_aem-av_scr&#8217;);%读取excel表格sheet为H_aem-av_scr的内容
  </div>
  
  <div>
    guidata(hObject,handles)
  </div>
  
  <div>
    % UIWAIT makes H_aem_av wait for user response (see UIRESUME)
  </div>
  
  <div>
    % uiwait(handles.figure1);
  </div>
  
  <div>
  </div>
  
  <div>
  </div>
  
  <div>
    % &#8212; Outputs from this function are returned to the command line.
  </div>
  
  <div>
    function varargout = H_aem_av_OutputFcn(hObject, eventdata, handles)
  </div>
  
  <div>
    % varargout  cell array for returning output args (see VARARGOUT);
  </div>
  
  <div>
    % hObject    handle to figure
  </div>
  
  <div>
    % eventdata  reserved &#8211; to be defined in a future version of MATLAB
  </div>
  
  <div>
    % handles    structure with handles and user data (see GUIDATA)
  </div>
  
  <div>
  </div>
  
  <div>
    % Get default command line output from handles structure
  </div>
  
  <div>
    varargout{1} = handles.output;
  </div>
  
  <div>
  </div>
  
  <div>
  </div>
  
  <div>
    % &#8212; Executes on selection change in popupmenu1.
  </div>
  
  <div>
    function popupmenu1_Callback(hObject, eventdata, handles)
  </div>
  
  <div>
    % hObject    handle to popupmenu1 (see GCBO)
  </div>
  
  <div>
    % eventdata  reserved &#8211; to be defined in a future version of MATLAB
  </div>
  
  <div>
    % handles    structure with handles and user data (see GUIDATA)
  </div>
  
  <div>
  </div>
  
  <div>
    % Hints: contents = cellstr(get(hObject,&#8217;String&#8217;)) returns popupmenu1 contents as cell array
  </div>
  
  <div>
    %        contents{get(hObject,&#8217;Value&#8217;)} returns selected item from popupmenu1
  </div>
  
  <div>
    str = get(hObject, &#8216;String&#8217;);
  </div>
  
  <div>
    val = get(hObject,&#8217;Value&#8217;);
  </div>
  
  <div>
    % Set current data to the selected data set.
  </div>
  
  <div>
    switch str{val};
  </div>
  
  <div>
    case &#8216;1e-6&#8217; % User selects peaks.
  </div>
  
  <div>
       handles.H_aem = 1e-6;
  </div>
  
  <div>
    case &#8216;3e-6&#8217; % User selects membrane.
  </div>
  
  <div>
       handles.H_aem = 3e-6;
  </div>
  
  <div>
    case &#8216;5e-6&#8217; % User selects sinc.
  </div>
  
  <div>
       handles.H_aem = 5e-6;
  </div>
  
  <div>
    case &#8216;7e-6&#8217; % User selects peaks.
  </div>
  
  <div>
       handles.H_aem = 7e-6;
  </div>
  
  <div>
    case &#8216;9e-6&#8217; % User selects membrane.
  </div>
  
  <div>
       handles.H_aem = 9e-6;
  </div>
  
  <div>
    end
  </div>
  
  <div>
    guidata(hObject,handles)
  </div>
  
  <div>
  </div>
  
  <div>
    % &#8212; Executes on selection change in popupmenu2.
  </div>
  
  <div>
    function popupmenu2_Callback(hObject, eventdata, handles)
  </div>
  
  <div>
    % hObject    handle to popupmenu2 (see GCBO)
  </div>
  
  <div>
    % eventdata  reserved &#8211; to be defined in a future version of MATLAB
  </div>
  
  <div>
    % handles    structure with handles and user data (see GUIDATA)
  </div>
  
  <div>
  </div>
  
  <div>
    % Hints: contents = cellstr(get(hObject,&#8217;String&#8217;)) returns popupmenu2 contents as cell array
  </div>
  
  <div>
    %        contents{get(hObject,&#8217;Value&#8217;)} returns selected item from popupmenu2
  </div>
  
  <div>
    str = get(hObject, &#8216;String&#8217;);
  </div>
  
  <div>
    val = get(hObject,&#8217;Value&#8217;);
  </div>
  
  <div>
    % Set current data to the selected data set.
  </div>
  
  <div>
    display(val);
  </div>
  
  <div>
    switch str{val};
  </div>
  
  <div>
    case &#8216;1e6&#8217; % User selects peaks.
  </div>
  
  <div>
       handles.av = 1e6;
  </div>
  
  <div>
    case &#8216;1e7&#8217; % User selects membrane.
  </div>
  
  <div>
       handles.av = 1e7;
  </div>
  
  <div>
    case &#8216;1e8&#8217; % User selects sinc.
  </div>
  
  <div>
       handles.av = 1e8;
  </div>
  
  <div>
    case &#8216;1e9&#8217; % User selects peaks.
  </div>
  
  <div>
       handles.av = 1e9;
  </div>
  
  <div>
    case &#8216;1e10&#8217; % User selects membrane.
  </div>
  
  <div>
       handles.av = 1e10;
  </div>
  
  <div>
    end
  </div>
  
  <div>
    guidata(hObject,handles)
  </div>
  
  <div>
  </div>
  
  <div>
    % &#8212; Executes on button press in pushbutton2.
  </div>
  
  <div>
    function pushbutton2_Callback(hObject, eventdata, handles)
  </div>
  
  <div>
    % hObject    handle to pushbutton2 (see GCBO)
  </div>
  
  <div>
    % eventdata  reserved &#8211; to be defined in a future version of MATLAB
  </div>
  
  <div>
    % handles    structure with handles and user data (see GUIDATA)
  </div>
  
  <div>
    [~,col_i]=find(strncmp(handles.txt, &#8216;Electrolyte current density norm (A/m^2), i electrolyte&#8217;,50));
  </div>
  
  <div>
    [~,col_vcell]=find(strncmp(handles.txt, &#8216;% V_cell&#8217;,8));
  </div>
  
  <div>
    [~,col_Haem]=find(strncmp(handles.txt, &#8216;H_aem&#8217;,5));
  </div>
  
  <div>
    [~,col_av]=find(strncmp(handles.txt, &#8216;av_scr&#8217;,6));
  </div>
  
  <div>
    data(:,1)=handles.num(:,col_av);%这一列是厚度m
  </div>
  
  <div>
    data(:,2)=handles.num(:,col_Haem);%这一列是湿度
  </div>
  
  <div>
    data(:,3)=handles.num(:,col_vcell);%这一列是输出电压（V）
  </div>
  
  <div>
    data(:,4)=handles.num(:,col_i);%这一列是电流
  </div>
  
  <div>
    data(:,4)=data(:,4)./10;%这一列是将电流从A/m^2换算为mA/cm^2
  </div>
  
  <div>
    data(:,5)=data(:,3).*data(:,4);%功率（mW/cm^2)
  </div>
  
  <div>
  </div>
  
  <div>
    %display(data);
  </div>
  
  <div>
    [a,~]=find(data(:,2)<(handles.H_aem*(1.+0.01))&data(:,2)>(handles.H_aem*(1.-0.01)));
  </div>
  
  <div>
    temp=data(a,:);
  </div>
  
  <div>
    %assignin(&#8216;base&#8217;, &#8216;temp&#8217;, temp);
  </div>
  
  <div>
    %display(temp);
  </div>
  
  <div>
    [b,~]=find(temp(:,1)<(handles.av*(1+0.01))&temp(:,1)>(handles.av*(1-0.01)));
  </div>
  
  <div>
    temp1=temp(b,:);
  </div>
  
  <div>
    %assignin(&#8216;base&#8217;, &#8216;temp1&#8217;, temp1);
  </div>
  
  <div>
    %display (temp1);
  </div>
  
  <div>
    [~,hLine1,hLine2] = plotyy(handles.axes1,temp1(:,4),temp1(:,3),temp1(:,4),temp1(:,5));
  </div>
  
  <div>
    display(handles.av);
  </div>
  
  <div>
    display(handles.H_aem);
  </div>
  
  <div>
    set(hLine1,&#8217;LineStyle&#8217;,&#8217;&#8211;&#8216;)
  </div>
  
  <div>
    set(hLine1,&#8217;Marker&#8217;,&#8217;o&#8217;)
  </div>
  
  <div>
    set(hLine2,&#8217;LineStyle&#8217;,&#8217;:&#8217;)
  </div>
  
  <div>
    set(hLine2,&#8217;Marker&#8217;,&#8217;*&#8217;)
  </div>
  
  <div>
    clear temp1;
  </div>
  
  <div>
    clear temp;
  </div>
  
  <div>
  </div>
  
  <div>
  </div>
  
  <div>
    % &#8212; Executes during object creation, after setting all properties.
  </div>
  
  <div>
    function popupmenu2_CreateFcn(hObject, eventdata, handles)
  </div>
  
  <div>
    % hObject    handle to popupmenu2 (see GCBO)
  </div>
  
  <div>
    % eventdata  reserved &#8211; to be defined in a future version of MATLAB
  </div>
  
  <div>
    % handles    empty &#8211; handles not created until after all CreateFcns called
  </div>
  
  <div>
  </div>
  
  <div>
    % Hint: popupmenu controls usually have a white background on Windows.
  </div>
  
  <div>
    %       See ISPC and COMPUTER.
  </div>
  
  <div>
    if ispc && isequal(get(hObject,&#8217;BackgroundColor&#8217;), get(0,&#8217;defaultUicontrolBackgroundColor&#8217;))
  </div>
  
  <div>
        set(hObject,&#8217;BackgroundColor&#8217;,&#8217;white&#8217;);
  </div>
  
  <div>
    end
  </div>
  
  <div>
  </div>
  
  <div>
  </div>
  
  <div>
    % &#8212; Executes during object creation, after setting all properties.
  </div>
  
  <div>
    function popupmenu1_CreateFcn(hObject, eventdata, handles)
  </div>
  
  <div>
    % hObject    handle to popupmenu1 (see GCBO)
  </div>
  
  <div>
    % eventdata  reserved &#8211; to be defined in a future version of MATLAB
  </div>
  
  <div>
    % handles    empty &#8211; handles not created until after all CreateFcns called
  </div>
  
  <div>
  </div>
  
  <div>
    % Hint: popupmenu controls usually have a white background on Windows.
  </div>
  
  <div>
    %       See ISPC and COMPUTER.
  </div>
  
  <div>
    if ispc && isequal(get(hObject,&#8217;BackgroundColor&#8217;), get(0,&#8217;defaultUicontrolBackgroundColor&#8217;))
  </div>
  
  <div>
        set(hObject,&#8217;BackgroundColor&#8217;,&#8217;white&#8217;);
  </div>
  
  <div>
    end
  </div>
  
  <div>
  </div>
  
  <div>
  </div>
  
  <div>
    % &#8212; Executes during object creation, after setting all properties.
  </div>
  
  <div>
    function axes1_CreateFcn(hObject, eventdata, handles)
  </div>
  
  <div>
    % hObject    handle to axes1 (see GCBO)
  </div>
  
  <div>
    % eventdata  reserved &#8211; to be defined in a future version of MATLAB
  </div>
  
  <div>
    % handles    empty &#8211; handles not created until after all CreateFcns called
  </div>
  
  <div>
  </div>
  
  <div>
    % Hint: place code in OpeningFcn to populate axes1
  </div>
  
  <div>
  </div>
</div>