---
title: Source Control-Plug-in-Glossar | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- glossary [Visual Studio SDK]
- source control plug-ins, glossary
ms.assetid: f224bbc9-38fc-4c80-ab09-51dcc8969f8e
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: b77cc0ea260ae86460de3c7a7752277a99291778
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="source-control-plug-in-glossary"></a>Datenquellen-Steuerelement-Plug-in-Glossar
Die folgenden hilfreich Begriffe und Definitionen beziehen sich auf die Datenquellen-Steuerelement-Plug-in SDK-Dokumentation.  
  
## <a name="definitions"></a>Definitionen  
 Checkin  
 Wenn ein Benutzer eine Arbeitskopie ändert, muss ein Benutzer Änderungen aus der Arbeitskopie in der zentrale Quellcodeverwaltungsrepository senden. Dies erstellt eine neue Revision der Datei, die von anderen Benutzern zur Verfügung steht. Dieser Vorgang wird eine Einchecken bezeichnet.  
  
 Auschecken  
 Der Vorgang für das Anfordern von einer Arbeitskopie aus dem Repository, informiert das Repository von Ihnen beabsichtigt, diese zu ändern. Eine Arbeitskopie zeigt den Status des Projekts zum Zeitpunkt der momentaufnahmeerstellung, die es ausgecheckt ist.  
  
 Client  
 Ein Programm, das Quellcodeverwaltungs-System verwendet. Im Rahmen dieser Dokumentation ist es der Visual Studio-IDE.  
  
 Kommentar  
 Eine Meldung, beschreibt die Änderungen, die ein Benutzer zu einer Version anfügen können, wenn ein Datenquellen-Steuerelement-Vorgang ausgeführt wird.  
  
 Konflikt  
 Eine Situation, wenn zwei Benutzer versuchen, Änderungen an der gleichen Region der gleichen Datei einchecken. In der Regel muss eine Zusammenführung durchgeführt werden.  
  
 Verzeichnis  
 Ein lokaler Ordner für die clientseitige wird ein Verzeichnis genannt. Dies ist die Kopie in der ein Benutzer tatsächlich ändert. Es kann viele Arbeitskopien eines bestimmten Projekts vorhanden sein. im Allgemeinen weist jeder Entwickler sein eigenes kopieren.  
  
 Get  
 Ein Get-Vorgang wird der Benutzer Arbeitskopie auf dem neuesten Stand mit der Repository-Kopie. Im Gegensatz zu einer Auschecken erfolgt ein Get, wenn der Benutzer die aktuellste Kopie benötigt einfach, aber keine Änderungen vornehmen möchte.  
  
 Versionsgeschichte  
 Es ist in der Regel eine Zusammenfassung aller Auschecken, Eincheckvorgänge, Updates, Tags und Versionen, die im Quellcodeverwaltungsrepository durchgeführt wird.  
  
 IDE  
 Im Allgemeinen bezieht sich auf der Visual Studio integrierten Entwicklungsumgebung. Allerdings könnte es auch auf andere Clientumgebungen beziehen, die von der Quelle Steuerelement-Plug-in-API erkannt.  
  
 Zusammenführen  
 Der Prozess, bei welcher, den Datenquelle der mindestens zwei Codedateien kombiniert werden, um eine neue Datei zu erstellen, die alle Funktionen aus vorherigen Dateien enthält. Dieses Konzept ist in der Versionskontrolle ausschlaggebend, in denen Entwickler von zwei oder mehr Dateien gleichzeitig arbeiten.  
  
 Projekt  
 Ein Quellverwaltungsordner wird häufig als ein Projekt bezeichnet. Dies verfügt nicht über Beziehung mit Projekte oder Projektmappen in Visual Studio.  
  
 Plug-In  
 Eine DLL, die Quellcodeverwaltungsfunktion bereitstellt, durch die Implementierung der Datenquellen-Steuerelement-Plug-in-API.  
  
 Repository  
 Die Masterkopie eine Quelle zu steuern, auf dem System speichert die vollständige Revisionsverlauf des Projekts. Jedes Projekt verfügt über genau ein Repository.  
  
 Revision  
 Eine Commit Änderung in der Versionsgeschichte einer Datei oder eine Gruppe von Dateien. Eine Revision wird eine Momentaufnahme eines Projekts ständig ändern.  
  
## <a name="see-also"></a>Siehe auch  
 [Quellcodeverwaltungs-Plug-Ins](../extensibility/source-control-plug-ins.md)