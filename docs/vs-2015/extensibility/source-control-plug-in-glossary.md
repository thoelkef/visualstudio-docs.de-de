---
title: Source-Control-Plug-in-Glossar | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- glossary [Visual Studio SDK]
- source control plug-ins, glossary
ms.assetid: f224bbc9-38fc-4c80-ab09-51dcc8969f8e
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f5120a5c6678cac32ef65e08ef7dc34649364cf9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68160605"
---
# <a name="source-control-plug-in-glossary"></a>Glossar für das Quellcodeverwaltungs-Plug-In
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die folgende nützliche Begriffe und Definitionen beziehen sich in der Source Control-Plug-in SDK-Dokumentation.  
  
## <a name="definitions"></a>Definitionen  
 Checkin  
 Wenn ein Benutzer eine Arbeitskopie Änderungen vornimmt, muss ein Benutzer Änderungen aus der Arbeitskopie in der Mitte Quellcodeverwaltungs-Repository senden. Dies erstellt eine neue Revision der Datei, die von anderen Benutzern zur Verfügung steht. Dieser Vorgang wird ein Eincheckvorgang bezeichnet.  
  
 Auschecken  
 Der Vorgang des Anforderung einer Arbeitskopie aus dem Repository, informiert das Repository von Ihrer Absicht entspricht, die sie ändern. Eine Arbeitskopie spiegelt wider, den Zustand des Projekts zum Zeitpunkt der, die sie ausgecheckt wird.  
  
 Client  
 Ein Programm, das Quellcodeverwaltungs-System verwendet. In dieser Dokumentation ist es die Visual Studio-IDE.  
  
 Kommentar  
 Eine Meldung zur Beschreibung der Änderungen, die ein Benutzer zu einer Überarbeitung anfügen können, wenn Sie ein Quellcodeverwaltungsvorgang ausgeführt wird.  
  
 Konflikt  
 Eine Situation, wenn zwei Benutzer versuchen, Änderungen an der gleichen Region der gleichen Datei zu überprüfen. In der Regel muss ein Mergevorgang ausgeführt werden.  
  
 Verzeichnis  
 Ein lokaler Ordner für die clientseitige wird als Verzeichnis bezeichnet. Hierbei handelt es sich um die Kopie, in der ein Benutzer tatsächlich Änderungen vornimmt. Es kann viele Arbeitskopien von einem bestimmten Projekt vorhanden sein. Jeder Entwickler hat in der Regel ein eigenes kopieren.  
  
 Get  
 Ein Get-Vorgang bringt des Benutzers Arbeitskopie auf dem neuesten Stand mit der Kopie des Repositorys. Im Gegensatz zu einer ausgecheckten Element gehört wird ein Get ausgeführt, wenn der Benutzer einfach die aktuelle Kopie benötigt, aber keine Änderungen vornehmen will.  
  
 Versionsgeschichte  
 Es ist in der Regel einen Überblick über alle Auschecken, Eincheckvorgänge, Updates, Tags und Versionen, die in den Quellcodeverwaltungs-Repository durchgeführt.  
  
 IDE  
 In der Regel verweist auf der Visual Studio integrierten Entwicklungsumgebung. Es kann jedoch auch andere Client-Umgebungen verweisen, die von der Quelle-Plug-in-API erkannt.  
  
 Merge  
 Der Prozess, bei der, den Quelle mindestens zwei Codedateien kombiniert werden, um eine neue Datei zu erstellen, die alle Funktionen von vorherigen-Dateien enthält. Dieses Konzept ist wichtig, in der Versionskontrolle arbeiten, in denen zwei oder mehr Entwickler gleichzeitig an Dateien.  
  
 Projekt  
 Ein Ordner für die quellcodeverwaltung wird häufig als Projekt bezeichnet. Dies muss keine Beziehung mit der Projekte oder Projektmappen in Visual Studio.  
  
 Plug-In  
 Eine DLL, die Quellcodeverwaltungsfunktionen bereitstellt, durch die Implementierung der Source-Plug-in-API.  
  
 Repository  
 Die Masterkopie, in dem Quellcode System, speichert den Verlauf eines Projekts vollständige Revision. Jedes Projekt verfügt über genau ein Repository.  
  
 Revision  
 Eine fortgeschriebene Änderung in der Versionsgeschichte einer Datei oder einer Gruppe von Dateien. Eine Revision wird eine Momentaufnahme in einem Projekt auf kontinuierlich ändern.  
  
## <a name="see-also"></a>Siehe auch  
 [Quellcodeverwaltungs-Plug-Ins](../extensibility/source-control-plug-ins.md)
