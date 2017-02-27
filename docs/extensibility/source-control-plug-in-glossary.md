---
title: "Source Control-Plug-in-Glossar | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Glossar [Visual Studio SDK]"
  - "Source Control-Plug-ins, Glossar"
ms.assetid: f224bbc9-38fc-4c80-ab09-51dcc8969f8e
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# Source Control-Plug-in-Glossar
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die folgenden hilfreiche Begriffe und Definitionen beziehen sich auf die Datenquellen\-Steuerelement\-Plug\-in SDK\-Dokumentation.  
  
## Definitionen  
 Einchecken  
 Wenn ein Benutzer eine Arbeitskopie ändert, muss ein Benutzer über die Arbeitskopie in zentralen Quellcodeverwaltungsrepository Änderungen senden. Dies erstellt eine neue Version der Datei, die für andere Benutzer verfügbar ist. Dieser Vorgang wird eine Checkin bezeichnet.  
  
 Auschecken  
 Der Vorgang der Anforderung einer Arbeitskopie aus dem Repository, informiert das Repository für Ihre Absicht ändern. Eine Arbeitskopie zeigt den Status des Projekts zum Zeitpunkt der, die sie ausgecheckt wird.  
  
 Client  
 Ein Programm, das Quellcodeverwaltungssystem verwendet. Im Rahmen dieser Dokumentation ist es der Visual Studio\-IDE.  
  
 Kommentar  
 Eine Meldung angezeigt, die Änderungen, die ein Benutzer zu einer Überarbeitung anfügen kann, wenn ein Vorgang von Quellcode erfolgt.  
  
 Konflikt  
 Eine Situation, wenn zwei Benutzer versuchen, dieselbe Region aus der gleichen Datei einchecken. In der Regel muss eine Zusammenführung ausgeführt werden.  
  
 Verzeichnis  
 Ein lokaler Ordner für die clientseitige wird ein Verzeichnis genannt. Dies ist die Kopie in der ein Benutzer Änderungen tatsächlich vornimmt. Es kann viele Arbeitskopien eines Projekts vorhanden sein. Jeder Entwickler hat im Allgemeinen ein eigenes kopieren.  
  
 Get  
 Ein Get\-Vorgang bringt des Benutzers Arbeitskopie aktuell mit der Kopie des Repository. Im Gegensatz zum Auschecken erfolgt ein Get, wenn der Benutzer einfach die neueste Kopie benötigt jedoch keine Änderungen vornehmen will.  
  
 Versionsgeschichte  
 Es ist in der Regel eine Zusammenfassung aller Auschecken, Eincheckvorgänge, Updates, Tags und Versionen im Quellcodeverwaltungsrepository durchgeführt wird.  
  
 IDE  
 Im Allgemeinen bezieht sich auf Visual Studio Integrated Development Environment. Jedoch konnte es auch auf andere Clientumgebungen verweisen, die von der Quelle Steuerelement\-Plug\-in\-API erkannt.  
  
 Zusammenführen  
 Der Prozess, in dem zwei oder mehr, den Quellcode Codedateien kombiniert werden, um eine neue Datei zu erstellen, die alle Funktionen aus früheren Dateien enthält. Dieses Konzept ist unerlässlich, Versionskontrolle, in dem zwei oder mehr Entwickler auf Dateien gleichzeitig arbeiten.  
  
 Projekt  
 Ein Quellcodeverwaltungsordner wird häufig als ein Projekt bezeichnet. Dies muss nicht Beziehung mit Projekten oder Projektmappen in Visual Studio.  
  
 Plug\-In  
 Eine DLL, die die Quellcodeverwaltungsfunktionen bietet die Source Control\-Plug\-in\-API implementiert.  
  
 Repository  
 Die master\-Kopie, in denen ein System von Quellcode, werden vollständige Revisionsverlauf des Projekts gespeichert. Jedes Projekt verfügt über genau ein Repository.  
  
 Revision  
 Eine fortgeschriebene Änderung in der Versionsgeschichte einer Datei oder eine Gruppe von Dateien. Eine Version ist eine Momentaufnahme eines Projekts kontinuierlich ändern.  
  
## Siehe auch  
 [Source Control\-Plug\-ins](../extensibility/source-control-plug-ins.md)