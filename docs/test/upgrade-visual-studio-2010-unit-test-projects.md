---
title: Upgrade der Komponententestprojekte von Visual Studio 2010 | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f1502b51-d6db-4894-9fbf-4a5723e4bb1a
caps.latest.revision: 8
ms.author: mlearned
manager: douge
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: c5b99a1f1661e412ae097660298942ebb89b15b1
ms.lasthandoff: 02/22/2017

---
# <a name="upgrade-visual-studio-2010-unit-test-projects"></a>Upgrade der Komponententestprojekte von Visual Studio 2010
Zu [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] gehört die Testprojektkompatibilität mit Testprojekten von [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] SP1. So können beispielsweise mit [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] SP1 erstellte Testprojekte ohne Upgrade mit [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] geöffnet werden. Somit ist es möglich, dass Teammitglieder sowohl mit [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] SP1 als auch mit [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] an ein und demselben Testprojekt arbeiten. Weitere Informationen finden Sie unter [Upgrading tests from Visual Studio 2010 (Aktualisieren von Tests von Visual Studio 2010)](http://msdn.microsoft.com/en-us/e9c8b7f6-bd72-448e-8edb-d090dcc5cf52).  
  
 Mit [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] werden für Komponententests verschiedene Änderungen eingeführt. Aufgrund dieser Änderungen sollten Sie die Kompatibilitätsprobleme kennen, die zwischen früheren Versionen von Visual Studio und [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] auftreten. Eine wichtige Änderung bei Komponententests ist die, dass [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] jetzt mehrere Testprojektvorlagen enthält, darunter auch eine Komponententestprojektvorlage. Diese neue Komponententestprojektvorlage enthält neue Komponententests. Darüber hinaus können Komponententests auch in eine andere Komponententestvorlage mit dem Namen Projektvorlage für Tests der programmierten UI aufgenommen werden. Weitere Informationen finden Sie unter [Upgrading Tests from Earlier Versions of Visual Studio (Upgrade der Tests von früheren Visual Studio-Versionen)](http://msdn.microsoft.com/en-us/e9c8b7f6-bd72-448e-8edb-d090dcc5cf52). In den neuen Komponententestprojekten ist die Datei mit Testeinstellungen nicht mehr standardmäßig enthalten. Dadurch wurde die Leistung der Komponententests verbessert. Zur Gewährleistung der Kompatibilität können Sie dennoch bereits vorhandene Testprojekte verwenden, die Sie mit Visual Studio 2010 erstellt haben. Es wird jedoch empfohlen, die mit dem Testprojekt verknüpfte Testeinstellungsdatei zur Verbesserung der Leistung zu entfernen, sofern Sie diese Datei nicht für einen bestimmten Zweck benötigen. So sollten Sie die Testeinstellungsdatei beispielsweise nicht entfernen, wenn die Komponententests in einer verteilten Umgebung ausgeführt werden oder wenn bestimmte Diagnosedaten erfasst werden müssen. Bei Bedarf können Sie auch die neue Komponententestprojektvorlage oder die Projektvorlage für Tests der programmierten UI manuell mit einer Testeinstellungsdatei erweitern.  
  
> [!NOTE]
>  Vorhandene Komponententests in [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] SP1-Testprojekten können problemlos in [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] SP1 und [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] verwendet werden. Beim Öffnen eines Visual Studio 2010-Testprojekts mit Ihren Komponententests in [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] oder umgekehrt werden an den Testprojektdateien keine Änderungen vorgenommen.  
  
> [!CAUTION]
>  C++/CLI-Projekte, die das 11.0-Toolset nutzen, d.h. in Visual Studio 2012 erstellte Projekte, können in Visual Studio 2010 nicht geöffnet werden. Diese Einschränkung gilt für alle C++/CLI-Projekte, nicht nur für C++/CLI-Komponententestprojekte.  
  
> [!NOTE]
>  Die neuen Komponententests können mit dem Befehl vstest.console.exe über die Befehlszeile ausgeführt werden. Weitere Informationen zur Verwendung des Befehls vstest.console.exe finden Sie unter [VSTest.Console.exe command-line options (Befehlszeilenoptionen für VSTest.Console.exe )](/devops-test-docs/test/vstest-console-exe-command-line-options). Alternativ können Sie den Befehl mit dem Hilfe-Schalter ausführen: **vstest.console.exe /?**. Ihre vorhandenen Komponententests können Sie weiterhin mit dem Befehl MStest.exe ausführen. Weitere Informationen finden Sie unter [Run automated tests from the command line using MSTest (Ausführen von automatisierten Tests über die Befehlszeile mithilfe von MSTest)](/devops-test-docs/test/run-automated-tests-from-the-command-line-using-mstest) und [Befehlszeilenoptionen für MSTest.exe](/devops-test-docs/test/mstest-exe-command-line-options).  
  
 Eine weitere wichtige Änderung stellt der neue Test-Explorer dar. Einige Testfenster, wie etwa das Testansichtsfenster, die Sie von früheren Versionen von Visual Studio kennen, sind in [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] nicht mehr enthalten. Mit dem Test-Explorer können Entwickler und Teams die Komponententests besser in ihre Verfahren für die Softwareentwicklung integrieren. Weitere Informationen finden Sie unter [Run unit tests with Test Explorer (Ausführen von Komponententests mit dem Test-Explorer)](../test/run-unit-tests-with-test-explorer.md).  
  
## <a name="compatibility-issues-between-visual-studio-2010-sp1-and-visual-studio-2012"></a>Kompatibilitätsprobleme mit Visual Studio 2010 SP1 und Visual Studio 2012  
 Folgende Punkte sollten Sie bei der Migration von Komponententests zwischen Visual Studio 2010 SP1 und [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] beachten:  
  
|Komponententestfunktionen|Problem|Lösung|  
|-----------------------------|-----------|--------------|  
|Testlisten (.vsmdi-Dateien) gibt es in [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] nicht mehr.|In Visual Studio können keine neuen Testlisten (.vsmdi-Dateien) mehr erstellt oder ausgeführt werden. **Tipp:** Testkategorien bieten mehr Flexibilität als die Testlistenfunktion in früheren Versionen von Microsoft Visual Studio. Sie können mit Testkategorien logische Operatoren verwenden, um Tests aus mehreren Kategorien gemeinsam auszuführen oder um die Ausführung auf Tests zu beschränken, die mehreren Kategorien angehören. Testkategorien können ganz einfach beim Erstellen der Testmethoden hinzugefügt werden. Sie müssen keine Testlisten mehr verwalten, nachdem Sie die Testmethoden erstellt haben. Bei Verwendung von Testkategorien müssen Sie die Datei **\<Projektmappenname>.vsmdi**, in der die Testlisten verwaltet werden, nicht mehr ein- bzw. auschecken. Weitere Informationen finden Sie unter [Defining Test Categories to Group Your Tests (Definieren von Testkategorien zum Gruppieren von Tests)](/devops-test-docs/test/defining-test-categories-to-group-your-tests).|- Zur Gewährleistung der Kompatibilität mit den vorhandenen Testprojekten, bei denen Testlisten verwendet werden, können .vsmdi-Dateien nach wie vor mit Visual Studio bearbeitet werden.<br />- In Visual Studio können migrierte Testlisten zwar nicht ausgeführt werden. Dies ist jedoch mit dem Befehl mstest.exe über die Befehlszeile möglich. Weitere Informationen hierzu finden Sie unter [Run automated tests from the command line using MSTest (Ausführen von automatisierten Tests über die Befehlszeile mit MSTest)](/devops-test-docs/test/run-automated-tests-from-the-command-line-using-mstest)<br />- Wenn Sie bisher eine Testliste in der Builddefinition verwendet haben, können Sie diese Testliste weiterhin verwenden. Weitere Informationen hierzu finden Sie unter [How to: Configure and Run Scheduled Tests After Building Your Application (Vorgehensweise: Konfigurieren und Ausführen von geplanten Test nach dem Erstellen der Anwendung)](http://msdn.microsoft.com/en-us/32acfeb1-b1aa-4afb-8cfe-cc209e6183fd) und unter [Run tests in your build process (Ausführen von Tests im Buildprozess)](http://msdn.microsoft.com/Library/d05743a1-c5cf-447e-bed9-bed3cb595e38).|  
|Private Accessoren werden in [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] nicht mehr verwendet.<br /><br /> In früheren Versionen von Visual Studio konnte mithilfe von Publicize eine interne API (Application Programming Interface) angegeben und die entsprechende öffentliche API erstellt werden, die in Tests aufgerufen werden konnte, die ihrerseits die interne API des Projekts aufrufen. Anschließend konnten mittels Codegenerierung Test-Stubs erstellt und in diesen Stubs Codeausschnitte generiert werden.|Private Accessoren können nun nicht mehr erstellt werden.|<ul><li>Visual Studio 2010-Testprojekte werden in [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] kompiliert und ausgeführt. Der Build enthält Ausgabewarnungen.</li><li>Wenn Sie interne APIs testen müssen, haben Sie folgende Möglichkeiten:<br /><br /> <ul><li>Verwenden Sie die <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PrivateObject>-Klasse für den Zugriff auf interne und private APIs in Ihrem Code. Sie finden diese in der Microsoft.VisualStudio.QualityTools.UnitTestFramework.dll-Assembly.</li><li>Erstellen Sie ein Reflektionsframework, das den Code für den Zugriff auf interne und private APIs spiegelt.</li><li>Beim Zugriff auf internen Code können Sie möglicherweise mit <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> auf Ihre APIs zugreifen, sodass Ihr Testcode Zugriff auf die internen APIs hat.</li></ul></li></ul>|  
|Testauswirkung wurde entfernt.|||  
|Testlaufergebnisse werden mittels TRX-Protokolle über den Test-Explorer gemeinsam genutzt.||TRX-Protokolle können nach wie vor sowohl über die Befehlszeile als auch über Team Build abgerufen werden.|  
  
## <a name="see-also"></a>Siehe auch  
 [Portieren, Migrieren und Upgraden von Visual Studio-Projekten](../porting/porting-migrating-and-upgrading-visual-studio-projects.md)   
 [Unit Test Your Code (Komponententest für Code)](../test/unit-test-your-code.md)   
 [Upgrading Tests from Earlier Versions of Visual Studio (Upgrade der Tests von früheren Visual Studio-Versionen)](http://msdn.microsoft.com/en-us/e9c8b7f6-bd72-448e-8edb-d090dcc5cf52)   
 [Upgrade der Tests der programmierten UI von Visual Studio 2010](../test/upgrading-coded-ui-tests-from-visual-studio-2010.md)
