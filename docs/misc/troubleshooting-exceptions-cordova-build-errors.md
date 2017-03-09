---
title: "Problembehandlung bei Ausnahmen: Cordova-Buildfehler | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BLD102"
  - "BLD10205"
  - "BLD301"
  - "BLD401"
  - "BLDErr_Build_NodeMissing"
  - "BLDErr_BLD_Win8Required"
ms.assetid: 781c09e3-0704-4b30-9230-036cbdb2dff9
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
---
# Problembehandlung bei Ausnahmen: Cordova-Buildfehler
In diesem Thema sind einige der häufigsten Fehlermeldungen beschrieben, die möglicherweise angezeigt werden, wenn Sie Visual Studio\-Tools für Apache Cordova verwenden.  
  
-   [MSBUILD: Cordova-Buildfehler BLD102: 'config.xml' – keine entsprechende Datei bzw. kein entsprechendes Verzeichnis](#BLD102)  
  
-   [MSBUILD: Cordova-Buildfehler BLD301: Es wurde kein iOS-Remotebuild-Agent konfiguriert.](#BLD301)  
  
-   [MSBUILD: Cordova-Buildfehler BLD401: Modul '&lt;Modulname&gt;' wurde nicht gefunden.](#BLD401)  
  
-   [MSBUILD: Cordova-Buildfehler BLD10205: Installieren Sie das Android-Ziel](#BLD10205)  
  
-   [BLDErr_Build_NodeMissing: Pfad zur ausführbaren Datei "Node.js" konnte nicht ermittelt werden.](#BLDErr_Build_NodeMissing)  
  
-   [BLDErr_Build_Win8Required](#BLDErr_Build_Win8Required)  
  
 Weitere allgemeine Hilfe bei der Problembehandlung von Fehlern in Ihrer Cordova\-App finden Sie unter [Resolve build and deployment errors](https://taco.visualstudio.com/en-us/docs/resolving-build-errors/) \(Beheben von Build\- und Bereitstellungsfehlern\).  
  
##  <a name="BLD102"></a> MSBUILD: Cordova\-Buildfehler BLD102: 'config.xml' – keine entsprechende Datei bzw. kein entsprechendes Verzeichnis  
 Wenn dieser Fehler angezeigt wird, vergewissern Sie sich, dass Ihr Projekt eine „config.xml“\-Datei im Projektstammverzeichnis enthält, und vergewissern Sie sich, dass sich Ihr Projekt auf dem lokalen Computer, nicht auf einer Netzwerkfreigabe befindet.  
  
 Weitere Informationen hierzu finden Sie in diesem [StackOverflow\-Beitrag](http://stackoverflow.com/questions/27134007/new-cordova-project-gives-the-error-bld00102-no-such-file-or-directory-confi).  
  
##  <a name="BLD301"></a> MSBUILD: Cordova\-Buildfehler BLD301: Es wurde kein iOS\-Remotebuild\-Agent konfiguriert.  
 Die vollständige Fehlerzeichenfolge lautet:  
  
-   MSBUILD: Cordova\-Buildfehler BLD301: Es wurde kein iOS\-Remotebuild\-Agent konfiguriert. Konfigurieren Sie einen unter Extras \> Optionen \> Tools für Apache Cordova \> Remote\-Agent\-Konfiguration. Informationen und Alternativen finden Sie unter "http:\/\/go.microsoft.com\/fwlink\/?LinkID\=511904"  
  
 Informationen zum Installieren und Konfigurieren des Remotebuild\-Agents für iOS finden Sie unter [iOS Setup Guide](http://taco.visualstudio.com/en-us/docs/ios-guide/).  
  
##  <a name="BLD401"></a> MSBUILD: Cordova\-Buildfehler BLD401: Modul '\<Modulname\>' wurde nicht gefunden.  
 Die vollständige Fehlerzeichenfolge lautet:  
  
-   MSBUILD: Cordova\-Buildfehler BLD401: Fehler: BLD00401: Modul '\<Modulname\>' wurde nicht gefunden. Wechseln Sie zu Extras \-\-\> Optionen \-\-\> Tools für Apache Cordova \-\-\> Cordova\-Tools \-\-\> Cordova\-Cache leeren, und erstellen Sie den Build erneut.  
  
 Möglicherweise müssen Sie den Cache\-Inhalt löschen und vs\-tac erneut installieren. Weitere Informationen finden Sie unter [Erneutes Installieren von vs\-tac](http://taco.visualstudio.com/en-us/docs/configure-vs-tools-apache-cordova#vstac).  
  
 Nachdem Sie den Cache bereinigen, löschen Sie den Plattformordner im Projekt. Versuchen Sie anschließend erneut, einen Build erstellen.  
  
##  <a name="BLD10205"></a> MSBUILD: Cordova\-Buildfehler BLD10205: Installieren Sie das Android\-Ziel  
 Wenn dieser Fehler angezeigt wird, stellen Sie sicher, dass Sie die erforderlichen Abhängigkeiten für das ausgewählte Zielgerät mit dem Android SDK\-Manager \(SDK Manager.exe\) installieren.  
  
 Weitere Informationen zur erforderlichen API\-Ebene und weiteren Android SDK\-Komponenten finden Sie unter [Manuelles Installieren von Abhängigkeiten](http://taco.visualstudio.com/en-us/docs/configure-vs-tools-apache-cordova#ThirdParty).  
  
 Sie sollten auch den Speicherort überprüfen, in dem Visual Studio nach dem Android SDK sucht. Lesen Sie dazu [Überschreiben von Umgebungsvariablen des Systems](http://taco.visualstudio.com/en-us/docs/configure-vs-tools-apache-cordova#env-var).  
  
 Weitere Informationen zum Installieren der richtigen Komponenten zur Verwendung der Tools finden Sie unter [Drittanbietertools](http://taco.visualstudio.com/en-us/docs/install-vs-tools-apache-cordova#choose).  
  
##  <a name="BLDErr_Build_NodeMissing"></a> BLDErr\_Build\_NodeMissing: Pfad zur ausführbaren Datei "Node.js" konnte nicht ermittelt werden.  
 Wenn „Node.js“ in einem Nicht\-Standardspeicherort installiert wurde, kann es sein, dass Visual Studio die Datei nicht findet. Installieren Sie „Node.js“ im Standardspeicherort. Weitere Informationen hierzu finden Sie in diesem [StackOverflow\-Beitrag](http://stackoverflow.com/questions/32203992/vs2015-cordova-apps-blderr-build-nodemissing) sowie in diesem Artikel über [sicheres Aktualisieren von „Node.js“](http://taco.visualstudio.com/en-us/docs/change-node-version/).  
  
##  <a name="BLDErr_Build_Win8Required"></a> BLDErr\_Build\_Win8Required  
 Windows 8.1 ist erforderlich, wenn Windows das Ziel für eine App ist, die mithilfe von Visual Studio\-Tools für Apache Cordova erstellt wurde.