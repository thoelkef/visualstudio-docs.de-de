---
title: "Gewusst wie: Beschr&#228;nken der Instrumentation auf bestimmte DLLs | Microsoft Docs"
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
  - "Profilerstellungstools, Laufzeit-Profilerstellungssteuerung (Fenster)"
ms.assetid: 17c5996f-e3d0-4e44-b175-52b401b0f2d5
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Gewusst wie: Beschr&#228;nken der Instrumentation auf bestimmte DLLs
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Mit der Instrumentationsmethode zur Profilerstellung können Sie die Auflistung von Profilerstellungsdaten auf eine oder mehrere DLLs in einer Anwendung beschränken.  Um ein Profil für eine oder mehrere DLLs in einer Anwendung zu erstellen, können Sie eine Leistungssitzung erstellen, die die .dll\-Dateien als Ziele enthält.  Sie können die DLLs, für die Sie ein Profil erstellen möchten, als Projekte in einer [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Projektmappe oder als unabhängige binäre Dateien angeben.  
  
### So beschränken Sie die Instrumentation auf bestimmte DLLs in einer Visual Studio\-Projektmappe  
  
1.  Öffnen Sie die Projektmappe, die die DLL in [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)] enthält.  
  
2.  Klicken Sie im Menü **Analyse** auf **Leistungs\-Assistenten starten**.  
  
3.  Wählen Sie **Instrumentation** als Profilerstellungsmethode aus, und klicken Sie dann auf **Weiter**.  
  
4.  Wählen Sie in der Dropdownliste **Für welches der folgenden verfügbaren Ziele möchten Sie ein Profil erstellen?** den Namen des DLL\-Projekts aus, und klicken Sie dann auf **Weiter**.  
  
5.  Klicken Sie auf **Fertig stellen**, um den Assistenten zu beenden und die neue Leistungssitzung im Fenster **Leistungs\-Explorer**  anzuzeigen.  
  
6.  Klicken Sie mit der rechten Maustaste auf **Ziele**, und wählen Sie dann **Zielprojekt hinzufügen** aus.  
  
7.  Wählen Sie in der Liste **Zielprojekt hinzufügen** das ausführbare Projekt aus, das Sie zum Ausführen der DLL verwenden möchten.  
  
     Optional.  Sie können alle DLL\-Projekte hinzufügen, für die Sie ein Profil erstellen möchten.  
  
8.  Um die Datenauflistung für ein hinzugefügtes Projekt zu verhindern, klicken Sie mit der rechten Maustaste auf den Namen des Projekts, und deaktivieren Sie dann das Kontrollkästchen **Instrument**.  
  
### So geben Sie bestimmte DLLs für die Profilerstellung als unabhängige Binärdateien an  
  
1.  Öffnen Sie [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)].  
  
2.  Klicken Sie im Menü **Analyse** auf **Leistungs\-Assistenten starten**.  
  
3.  Wählen Sie in der Dropdownliste **Für welches der folgenden verfügbaren Ziele möchten Sie ein Profil erstellen?** die Option **Profil einer Dynamik Link Library \(.DLL\) erstellen** aus, und klicken Sie dann auf **Weiter**.  
  
4.  Führen Sie auf der zweiten Seite des Assistenten die folgenden Schritte aus:  
  
    -   Geben Sie den Pfad und den Dateinamen der .dll\-Datei, für die Sie ein Profil erstellen möchten, in das Feld **DLL\-Pfad** ein.  Sie können auch auf die Schaltfläche mit den Auslassungszeichen \(...\) klicken, um die Datei im Dialogfeld **Dynamic Link Library, für die ein Profil erstellt werden soll** zu suchen.  Beachten Sie, dass Sie die Kopie der DLL\-Datei angeben müssen, die durch die ausführbare Datei \(.exe\) gestartet wird, die Sie als Nächstes auswählen.  
  
    -   Geben Sie den Pfad und den Dateinamen der ausführbaren Datei \(.exe\), die die .dll ausführt, in das Feld **Pfad für ausführbare Datei** ein.  Sie können auch auf die Schaltfläche mit den Auslassungszeichen \(...\) klicken, um die Datei im Dialogfeld **Zu startende ausführbare Datei** zu suchen.  
  
    -   Optional.  Geben Sie im Feld **Befehlszeilenargumente** alle Befehlszeilenargumente ein, die Sie an die ausführbare Datei übergeben möchten.  Falls notwendig, geben Sie das Arbeitsverzeichnis für die Anwendung in **Arbeitsverzeichnis** an.  
  
    -   Klicken Sie auf **Weiter**.  
  
5.  Wählen Sie **Instrumentation** als Profilerstellungsmethode aus, und klicken Sie dann auf **Weiter**.  
  
6.  Klicken Sie auf **Fertig stellen**, um den Assistenten zu beenden und die neue Leistungssitzung im Fenster **Leistungs\-Explorer**  anzuzeigen.  
  
7.  Optional.  Um weitere DLL\-Dateien hinzuzufügen, klicken Sie mit der rechten Maustaste auf **Ziele**, und wählen Sie dann **Zielbinärdatei hinzufügen** aus.  Wählen Sie die Dateien im Dialogfeld **Zielbinärdatei hinzufügen** aus.  
  
    > [!NOTE]
    >  Geben Sie nicht die ausführbare Datei \(EXE\) an, die die DLLs ausführt.  
  
## Siehe auch  
 [Steuern der Datensammlung](../profiling/controlling-data-collection.md)   
 [Gewusst wie: Beschränken der Instrumentation auf bestimmte Funktionen](../profiling/how-to-limit-instrumentation-to-specific-functions.md)