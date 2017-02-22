---
title: "Gewusst wie: Festlegen von Berechtigungen f&#252;r die Profilerstellung | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Profilerstellung, Festlegen von Berechtigungen"
  - "Sicherheit [Visual Studio ALM], Festlegen von Berechtigungen"
  - "Berechtigungen [Visual Studio ALM], Profilerstellung"
  - "Profilerstellungstools, Festlegen von Berechtigungen für die Profilerstellung"
  - "Leistungstools, Festlegen von Berechtigungen für die Profilerstellung"
ms.assetid: 69f27896-8f46-4ef3-bfb7-726d95304f3a
caps.latest.revision: 23
caps.handback.revision: 23
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Gewusst wie: Festlegen von Berechtigungen f&#252;r die Profilerstellung
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In diesem Thema wird erläutert, wie ein Administrator eines Computers die für die Profilerstellung erforderlichen Sicherheitsberechtigungen einem Benutzer oder einer Gruppe zuweist, der bzw. die auf diesem Computer nicht über Administratorberechtigungen verfügt.  
  
 Einem grundlegenden Sicherheitsprinzip zufolge sollen Anwendungen nur mit den erforderlichen Berechtigungen ausgeführt werden.  Dieses Prinzip gilt auch für Benutzer.  Wenn ein Benutzer absolut effizient arbeiten kann, wenn er als Mitglied der Gruppe Benutzer statt als Mitglied der Gruppe Administratoren angemeldet ist, sollten ihm auch keine Administratorberechtigungen erteilt werden.  In der ersten Vorgehensweise, "So erstellen Sie ein Benutzerkonto mit Benutzerberechtigungen", wird das Erstellen eines Benutzerkontos für ein Mitglied der Gruppe Benutzer beschrieben.  
  
 **Voraussetzungen**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
 Mitglieder der Gruppe Benutzer müssen auf die Ordner und Dateien auf der Festplatte zugreifen können, die mit anderen Teammitglieder gemeinsam genutzt werden.  In der zweiten Vorgehensweise, "So erteilen Sie den Zugriff auf gemeinsam genutzte Projektdateien", wird das Erteilen des Zugriffs beschrieben.  
  
 Mitglieder der Benutzergruppe können die Profilerstellungstools ausführen, wenn ein Administrator ihnen den Zugriff auf den Softwaretreiber für die Profilierungstools gewährt.  In der letzten Vorgehensweise, "So erteilen Sie den Zugriff auf den Treiber für die Profilerstellung", wird das Erteilen des Zugriffs auf den Treiber beschrieben.  
  
> [!NOTE]
>  Sie benötigen Administratorberechtigungen, um die Schritte in diesen Vorgehensweisen ausführen zu können.  
  
### So erstellen Sie ein Benutzerkonto mit Benutzerberechtigungen  
  
1.  Klicken Sie mit der rechten Maustaste auf **Arbeitsplatz**, und klicken Sie auf **Verwalten**.  
  
     Das Dialogfeld **Computerverwaltung** wird geöffnet.  
  
2.  Erweitern Sie den Knoten **Lokale Benutzer und Gruppen**.  
  
3.  Klicken Sie mit der rechten Maustaste auf den Ordner **Benutzer**, und klicken Sie dann auf **Neuer Benutzer**.  
  
     Das Dialogfeld **Neuer Benutzer** wird angezeigt.  
  
4.  Geben Sie in die Felder dieses Dialogfelds die Informationen zu dem Benutzerkonto ein, das Sie gerade erstellen.  Legen Sie ein Kennwort fest.  Aktivieren Sie optional das Kontrollkästchen, das festlegt, dass der Benutzer bei der nächsten Anmeldung das Kennwort ändern muss.  
  
5.  Klicken Sie auf **Erstellen** und anschließend auf **Schließen**.  
  
     Der neue Benutzer wird in der Gruppe Benutzer angezeigt, einer Gruppe von Benutzern, die nicht über Administratorberechtigungen verfügen.  
  
### So erteilen Sie den Zugriff auf gemeinsam genutzte Projektdateien  
  
1.  In Windows Explorer \(oder im Datei\-Explorer\), suchen Sie den Stamm der Ordnerstruktur für die Projektdateien, die von diesem Benutzer und dem Projektteam gemeinsam genutzt werden.  
  
     Der Pfad dieses Ordners könnte folgendermaßen aussehen:  
  
    ```  
    D:\ourProject  
    ```  
  
2.  Klicken Sie mit der rechten Maustaste auf den Ordner, und klicken Sie dann auf **Eigenschaften**.  
  
     Das Dialogfeld **\<Ordnername\>\-Eigenschaften** wird.  
  
3.  Klicken Sie auf die Registerkarte **Sicherheit**.  
  
4.  Klicken Sie im Feld **Gruppen\- oder Benutzernamen** auf den Namen für das Konto des Benutzers.  
  
5.  Im Feld **Berechtigungen für \<Benutzername\>** wählen Sie das Kontrollkästchen für **Vollzugriff**.  
  
6.  Klicken Sie auf **OK**.  
  
     So wird dem Benutzer der Zugriff auf die gemeinsam genutzte Ordnerstruktur erteilt, an deren Anfang sich der in Schritt 5 ausgewählte Ordner befindet.  
  
### So erteilen Sie den Zugriff auf den Treiber für die Profilerstellung  
  
1.  Öffnen Sie eine Eingabeaufforderung als Administrator.  
  
2.  Wechseln Sie zu folgendem Verzeichnis:  
  
    ```  
    <drive>:\Program Files\Microsoft Visual Studio 10\Team Tools\Performance Tools  
    ```  
  
3.  Führen Sie den folgenden Befehl aus:  
  
    ```  
    vsperfcmd /admin:driver,start /admin:service,start  
    ```  
  
     Mithilfe dieses Befehls wird der Treiber für die Profilerstellungstools installiert und gestartet.  
  
     Durch diesen Befehl werden Treiber und Dienst für die Profilerstellung gestartet, sodass die Profilerstellungsfeatures auch Benutzern ohne Administratorrechte im Benutzerprozessbereich zur Verfügung stehen.  Der Befehl kann nur von einem Administrator ausgeführt werden und schlägt bei Benutzern ohne Administratorrechte fehl.  
  
     Damit die Auswirkungen der Ausführung dieses Schritts bei einem Neustart des Computers nicht rückgängig gemacht werden, müssen Sie den letzten Schritt in dieser Vorgehensweise ausführen.  
  
4.  Führen Sie den Befehl aus, um den Zugriff auf Treiberfunktionen für die Profilerstellung durch einen Benutzer oder eine Gruppe zu ermöglichen, der bzw. die keinen Administratorzugriff auf den Computer hat.  
  
    ```  
    vsperfcmd /admin:security,allow,<right[,right],<user name|group name>  
    ```  
  
     Dieser Befehl gewährt den \<Benutzername\> oder \<Gruppennamenkontozugriff\> für die Profilerstellungstools.  Die \<rechte\> Option bestimmt die Profilerstellungsfunktionalität fest, auf die der Benutzer zugreifen kann.  Die \<rechte\> Option kann eine oder mehrere der folgenden Werte sein:  
  
    -   FullAccess – ermöglicht den Zugriff auf alle Profilerstellungsmethoden, einschließlich der Erfassung von Leistungsdaten aus Services, Sampling und der sitzungsübergreifenden Profilerstellung.  
  
    -   SampleProfiling \- ermöglicht den Zugriff auf Sampling\-Profilerstellungsmethoden.  
  
    -   CrossSession – ermöglicht den Zugriff auf die sitzungsübergreifende Profilerstellung, die für Profilerstellungsdienste erforderlich ist.  
  
5.  \(Optional\) Damit die Ergebnisse der Ausführung eines der vorherigen Schritte nach einem Neustart des Computers erhalten bleiben, müssen Sie den folgenden Befehl ausführen:  
  
    ```  
    vsperfcmd /admin:driver,autostart,on  
    ```  
  
 Der angegebene Benutzer kann nun, sobald er angemeldet ist, die Profilerstellungstools ohne Administratorberechtigungen verwenden.  
  
## Siehe auch  
 [Konfigurieren von Leistungssitzungen](../profiling/configuring-performance-sessions.md)   
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilerstellung und Sicherheit in Windows Vista](../profiling/profiling-and-windows-vista-security.md)