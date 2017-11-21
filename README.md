OpenChart
=========

OpenChart is an open source Chart widget for Qt ♥

<img src='https://cn.pling.com/img//hive/content-pre3/157440-3.png'/>

***How to use?***

Download this project, and unzipp it, open ***" openCharts.pro "*** file into **qtCreator**

change Build mode to ***Release*** and click on ***Run*** button to compile

when you finish, create **new folders** and copy **"openchartplugin.dll"** and All **Headers File** in this structure:

<ul>
  OpenChart (folder)
  <ul>
      lib (folder)
      <ul>
        <li>openchartplugin.dll</li>
      </ul>
      include (folder)
      <ul>
        <li>global_header.h</li>
        <li>openchartplugin.h</li>
        <li>openchart.h</li>
        <li>qchartpiece.h</li>
      </ul>
  <ul>
</ul>

<br>
that's all :)

now to use this library in your project, go to .pro file and add this lines :

```qmake
INCLUDEPATH += "Your_Path/OpenChart/include"
LIBS += -L"Your_Path/OpenChart/lib"
LIBS += -lopenchartplugin

```
where ***Your_Path*** is a path to *OpenChart* folder, for example : *C:/ZakiProjects/OpenChart/include*.

don't forget to include openchart header in your source code:
```c++
#include <openchart.h>
```

This is a Simple Example :

```c++ 
mychart = new OpenChart(this);
    QMap<QString,double> map;

    map["Zakaria"] = 7500.00;
    map["Sarra"] = 1200.00;
    map["Ali"] = 220.50;
    map["Mona"] = 640.24;
    map["Khadija"] = 1000.00;
    map["Said"] = 2000.00;

    mychart->setTitle("Fisr Example Charts by Zaki");
    mychart->setTipo(OpenChart::Sectores_2D);

    // Add items to your chart object
    QMap<QString, double>::iterator i;
      for (i = map.begin(); i != map.end(); ++i){
          mychart->addItem(i.key(),i.value());
          //mychart->addItem(i.key(),i.value(),Qt::gray);
      }

    // Add your chart object to layout
    ui->gridLayout->addWidget(mychart);
```


my twitter : <a href='https://www.twitter.com/zaki_chahboun'>@Zaki_Chahboun</a>

Thanks to :
<a href='https://www.opendesktop.org/member/267936/'>0THEFOX0</a> ,
<a href='https://www.youtube.com/channel/UC6CdzK3QAxtr7giBwqk5eUA'>DuarteCorporation Channel</a>
