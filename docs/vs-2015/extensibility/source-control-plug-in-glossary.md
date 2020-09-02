---
title: Glossar für Quellcodeverwaltungs-Plug-ins | Microsoft-Dokumentation
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68160605"
---
# <a name="source-control-plug-in-glossary"></a>Glossar für das Quellcodeverwaltungs-Plug-In
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die folgenden hilfreichen Begriffe und Definitionen beziehen sich auf die SDK-Dokumentation für das Quellcodeverwaltungs-Plug-in.  
  
## <a name="definitions"></a>Definitionen  
 Checkin  
 Wenn ein Benutzer Änderungen an einer Arbeitskopie vornimmt, muss er Änderungen von der Arbeitskopie an das zentrale Quellcodeverwaltungs-Repository senden. Dadurch wird eine neue Revision der Datei erstellt, die anderen Benutzern zur Verfügung steht. Dieser Vorgang wird als Eincheck Vorgang bezeichnet.  
  
 Auschecken  
 Der Vorgang, bei dem eine Arbeitskopie aus dem Repository angefordert wird, um das Repository darüber zu informieren, dass es geändert werden soll. Eine Arbeitskopie gibt den Status des Projekts wieder, sobald es ausgecheckt ist.  
  
 Client  
 Ein Programm, das das Quell Code Verwaltungssystem verwendet. Der Zweck dieser Dokumentation ist die Visual Studio-IDE.  
  
 Comment  
 Eine Meldung, die die Änderungen beschreibt, die ein Benutzer an eine Revision anfügen kann, wenn ein Quell Code Verwaltungsvorgang ausgeführt wird.  
  
 Konflikt  
 Eine Situation, in der zwei Benutzer versuchen, Änderungen in denselben Bereich derselben Datei einzuchecken. In der Regel muss ein Merge ausgeführt werden.  
  
 Verzeichnis  
 Ein Client seitiger lokaler Ordner wird als Verzeichnis bezeichnet. Dies ist die Kopie, in der ein Benutzer tatsächlich Änderungen vornimmt. Es können viele Arbeitskopien eines bestimmten Projekts vorhanden sein. im allgemeinen verfügt jeder Entwickler über seine eigene Kopie.  
  
 Herunterladen  
 Mit einem Get-Vorgang wird die Arbeitskopie des Benutzers mit der Repository-Kopie auf den neuesten Stand bringen. Anders als bei einem Auscheck Vorgang wird ein Get-Vorgang ausgeführt, wenn der Benutzer einfach die neueste Kopie benötigt, aber keine Änderungen vornehmen soll.  
  
 Verlauf  
 Es handelt sich in der Regel um eine Zusammenfassung aller Auscheck Vorgänge, Eincheck Vorgänge, Updates, Tags und Releases, die im Quellcodeverwaltungs-Repository ausgeführt werden.  
  
 IDE  
 Bezieht sich im Allgemeinen auf die integrierte Entwicklungsumgebung von Visual Studio. Es kann jedoch auch auf andere Client Umgebungen verweisen, die die Quellcodeverwaltungs-Plug-in-API erkennen.  
  
 Merge  
 Der Prozess, in dem zwei oder mehr Quell Code Dateien kombiniert werden, um eine neue Datei zu erstellen, die alle Features aus früheren Dateien enthält. Dieses Konzept ist wichtig bei der Versionskontrolle, bei der zwei oder mehr Entwickler gleichzeitig an Dateien arbeiten.  
  
 Project  
 Ein Quell Code Verwaltungs Ordner wird häufig als Projekt bezeichnet. Dies hat keine Beziehung zu Projekten oder Projektmappen in Visual Studio.  
  
 Plug-In  
 Eine DLL, die Quell Code Verwaltungsfunktionen bereitstellt, indem die Quellcodeverwaltungs-Plug-in-API implementiert wird  
  
 Repository  
 Die Master Kopie, in der ein Quell Code Verwaltungssystem den vollständigen Revisions Verlauf eines Projekts speichert. Jedes Projekt verfügt über genau ein Repository.  
  
 Revision  
 Eine geänderte Änderung im Verlauf einer Datei oder einer Gruppe von Dateien. Eine Revision ist eine Momentaufnahme in einem ständig ändernden Projekt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Quellcodeverwaltungs-Plug-Ins](../extensibility/source-control-plug-ins.md)
