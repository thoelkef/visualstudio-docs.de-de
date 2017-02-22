---
title: "Exemplarische Vorgehensweise: Verwenden von Profiler-APIs | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Leistungstools, Exemplarische Vorgehensweisen"
  - "Profilerstellungstools, Exemplarische Vorgehensweisen"
ms.assetid: c2ae0b3e-a0ca-4967-b4df-e319008f520e
caps.latest.revision: 16
caps.handback.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Exemplarische Vorgehensweise: Verwenden von Profiler-APIs
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die exemplarische Vorgehensweise verwendet eine C\#\-Anwendung, um die Verwendung der APIs der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Profilerstellungstools zu veranschaulichen.  Sie verwenden die Profiler\-APIs zum Beschränken der Datenmenge, die während der instrumentierten Profilerstellung erfasst wird.  
  
 Die Schritte in dieser exemplarischen Vorgehensweise gelten allgemein für eine C\/C\+\+\-Anwendung.  Für jede Sprache muss die Buildumgebung entsprechend konfiguriert werden.  
  
 Normalerweise analysieren Sie zuerst die Anwendungsleistung mithilfe der Sampling\-Profilerstellung.  Wenn die Sampling\-Profilerstellung keine Informationen zur genauen Bestimmung eines Leistungsengpasses liefert, können anhand der instrumentierten Profilerstellung detailliertere Informationen abgerufen werden.  Die instrumentierte Profilerstellung ist sehr hilfreich beim Untersuchen der Threadinteraktion.  
  
 Eine größere Detailstufe bedeutet jedoch, dass mehr Daten erfasst werden.  Sie werden vielleicht feststellen, dass bei der instrumentierten Profilerstellung große Datendateien erzeugt werden.  Außerdem wirkt sich die Instrumentierung auch stärker auf die Anwendungsleistung aus.  Weitere Informationen finden Sie unter [Grundlagen zu Instrumentationsdatenwerten](../profiling/understanding-instrumentation-data-values.md) und unter [Grundlagen zu Samplingdatenwerten](../profiling/understanding-sampling-data-values.md).  
  
 Mit dem Visual Studio\-Profiler können Sie die Datenerfassung einschränken.  Diese exemplarische Vorgehensweise ist ein Beispiel dafür, wie die Datenerfassung mit den Profiler\-APIs eingeschränkt wird.  Der Visual Studio\-Profiler stellt eine API bereit, mit der die Datenerfassung aus einer Anwendung heraus gesteuert wird.  
  
 Bei systemeigenem Code befinden sich die Visual Studio\-Profiler\-APIs in VSPerf.dll.  Die Headerdatei VSPerf.h und die Importbibliothek VSPerf.lib befinden sich im Verzeichnis Microsoft Visual Studio 9\\Team Tools\\Performance Tools.  
  
 Bei verwaltetem Code befinden sich die Profiler\-APIs in Microsoft.VisualStudio.Profiler.dll.  Diese DLL befindet sich im Verzeichnis Microsoft Visual Studio 9\\Team Tools\\Performance Tool.  Weitere Informationen finden Sie unter <xref:Microsoft.VisualStudio.Profiler>.  
  
## Vorbereitungsmaßnahmen  
 In dieser exemplarischen Vorgehensweise wird davon ausgegangen, dass die ausgewählte Entwicklungsumgebung für die Unterstützung von Debuggen und Sampling konfiguriert ist.  Die folgenden Themen enthalten eine Übersicht über diese Voraussetzungen:  
  
 [Gewusst wie: Auswählen von Sammlungsmethoden](../profiling/how-to-choose-collection-methods.md)  
  
 [Gewusst wie: Verweisen auf Windows\-Symbolinformationen](../profiling/how-to-reference-windows-symbol-information.md)  
  
 Wenn der Profiler gestartet wird, werden standardmäßig Daten auf globaler Ebene erfasst.  Durch den folgenden Code am Anfang des Programms wird die globale Profilerstellung deaktiviert.  
  
```  
DataCollection.StopProfile(  
ProfileLevel.Global,  
DataCollection.CurrentId);  
```  
  
 Sie können die Datenerfassung in der Befehlszeile deaktivieren, ohne einen API\-Aufruf auszuführen.  Bei den folgenden Schritten wird vorausgesetzt, dass die Befehlszeilen\-Buildumgebung für die Ausführung sowohl von Profilerstellungs\- als auch von Entwicklungstools konfiguriert ist.  Dies schließt die für VSInstr und VSPerfCmd erforderlichen Einstellungen ein.  Siehe Profilerstellungstools für die Befehlszeile.  
  
## Beschränken der Datenerfassung mit Profiler\-APIs  
  
#### So erstellen Sie den Code für die Profilerstellung  
  
1.  Erstellen Sie je nach Ihren Anforderungen ein neues C\#\-Projekt in Visual Studio, oder verwenden Sie ein Befehlszeilenbuild.  
  
    > [!NOTE]
    >  Der Build muss auf die Microsoft.VisualStudio.Profiler.dll\-Bibliothek verweisen, die sich im Verzeichnis Microsoft Visual Studio \<Version\> Professional Edition 9\\Team Tools\\Performance Tools befindet.  
  
2.  Kopieren und fügen Sie den folgenden Code in das Projekt ein:  
  
    ```  
    using System;  
    using System.Collections.Generic;  
    using System.Text;  
    using Microsoft.VisualStudio.Profiler;  
  
    namespace ConsoleApplication2  
    {  
        class Program  
        {  
            public class A  
            {  
             private int _x;  
  
             public A(int x)  
             {  
              _x = x;  
             }  
  
             public int DoNotProfileThis()  
             {  
              return _x * _x;  
             }  
  
             public int OnlyProfileThis()  
             {  
              return _x + _x;  
             }  
  
             public static void Main()  
             {  
            DataCollection.StopProfile(  
            ProfileLevel.Global,  
            DataCollection.CurrentId);  
              A a;  
              a = new A(2);  
              int x;      
              Console.WriteLine("2 square is {0}", a.DoNotProfileThis());  
              DataCollection.StartProfile(  
                  ProfileLevel.Global,  
                  DataCollection.CurrentId);  
              x = a.OnlyProfileThis();  
              DataCollection.StopProfile(  
                  ProfileLevel.Global,   
                  DataCollection.CurrentId);  
              Console.WriteLine("2 doubled is {0}", x);  
             }  
            }  
  
        }  
    }  
    ```  
  
#### So erfassen und zeigen Sie Daten in der Visual Studio\-IDE an  
  
1.  Öffnen Sie die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-IDE.  Zeigen Sie im Menü **Analyse** auf **Profiler**, und klicken Sie dann auf **Neue Leistungssitzung**.  
  
2.  Fügen Sie die kompilierte Binärdatei der Liste **Ziele**  im Fenster **Leistungs\-Explorer** hinzu.  Klicken Sie mit der rechten Maustaste auf **Ziele**, und klicken Sie dann auf **Zielbinärdatei hinzufügen**.  Suchen Sie die Binärdatei im Dialogfeld **Zielbinärdatei hinzufügen**, und klicken Sie dann auf **Öffnen**.  
  
3.  Wählen Sie aus der Liste **Methode** auf der Symbolleiste **Leistungs\-Explorer Instrumentation** aus.  
  
4.  Klicken Sie auf **Mit Profilerstellung starten**.  
  
     Der Profiler instrumentiert die Binärdatei, führt sie aus und erstellt eine Leistungsberichtsdatei.  Die Leistungsberichtsdatei wird im Knoten **Berichte** des **Leistungs\-Explorers** angezeigt.  
  
5.  Öffnen Sie die resultierende Leistungsberichtsdatei.  
  
 Wenn der Profiler gestartet wird, werden standardmäßig Daten auf globaler Ebene erfasst.  Durch den folgenden Code am Anfang des Programms wird die globale Profilerstellung deaktiviert.  
  
```  
DataCollection.StopProfile(  
ProfileLevel.Global,  
DataCollection.CurrentId);  
```  
  
#### So erfassen und zeigen Sie Daten in der Befehlszeile an  
  
1.  Kompilieren Sie eine Debugversion des oben in dieser exemplarischen Vorgehensweise unter "So erstellen Sie den Code für die Profilerstellung" erstellten Beispielcodes.  
  
2.  Zur Profilerstellung für eine verwaltete Anwendung geben Sie den folgenden Befehl ein, um die entsprechenden Umgebungsvariablen festzulegen:  
  
     VsPefCLREnv \/traceon  
  
3.  Geben Sie den folgenden Befehl ein: filename.exe VSInstr \<\>  
  
4.  Geben Sie den folgenden Befehl ein: VSPerfCmd \/start:trace \/output:\<Dateiname.vsp\>  
  
5.  Geben Sie den folgenden Befehl ein: VSPerfCmd \/globaloff  
  
6.  Führen Sie das Programm aus.  
  
7.  Geben Sie den folgenden Befehl ein: VSPerfCmd \/shutdown  
  
8.  Geben Sie den folgenden Befehl ein: VSPerfReport \/calltrace:\<Dateiname.vsp\>  
  
     Eine CSV\-Datei wird mit den resultierenden Leistungsdaten im aktuellen Verzeichnis erstellt.  
  
## Siehe auch  
 <xref:Microsoft.VisualStudio.Profiler>   
 [Referenz zu Profiler\-APIs in Visual Studio \(systemeigen\)](../profiling/visual-studio-profiler-api-reference-native.md)   
 [Erste Schritte](../profiling/getting-started-with-performance-tools.md)   
 [Profilerstellung mithilfe der Befehlszeile](../profiling/using-the-profiling-tools-from-the-command-line.md)