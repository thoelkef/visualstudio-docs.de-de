---
title: Source-Control-Plug-in-Glossar | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- glossary [Visual Studio SDK]
- source control plug-ins, glossary
ms.assetid: f224bbc9-38fc-4c80-ab09-51dcc8969f8e
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 47488621fe3e5167e00442e1ca971ef923d9b25c
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66331908"
---
# <a name="source-control-plug-in-glossary"></a>Glossar für das Quellcodeverwaltungs-Plug-In
Die folgende nützliche Begriffe und Definitionen beziehen sich in der Source Control-Plug-in SDK-Dokumentation.

## <a name="definitions"></a>Definitionen
 Einchecken, wenn ein Benutzer eine Arbeitskopie ändert, muss ein Benutzer Änderungen aus der Arbeitskopie in der Mitte Quellcodeverwaltungs-Repository senden. Dies erstellt eine neue Revision der Datei, die von anderen Benutzern zur Verfügung steht. Dieser Vorgang wird ein Eincheckvorgang bezeichnet.

 Sehen Sie das Act eine Arbeitskopie anfordern, aus dem Repository, informiert das Repository von Ihrer Absicht entspricht, die sie ändern. Eine Arbeitskopie spiegelt wider, den Zustand des Projekts zum Zeitpunkt der, die sie ausgecheckt wird.

 Ein Clientprogramm, das Quellcodeverwaltungs-System verwendet. In dieser Dokumentation ist es die Visual Studio-IDE.

 Kommentar eine Meldung, die zur Beschreibung der Änderungen, die ein Benutzer zu einer Überarbeitung anfügen können, wenn Sie ein Quellcodeverwaltungsvorgang ausgeführt wird.

 Konflikt ein Fall, wenn zwei Benutzer versuchen, überprüfen Sie die im ändert sich in derselben Region der gleichen Datei. In der Regel muss ein Mergevorgang ausgeführt werden.

 Eine clientseitige lokale Verzeichnisordner wird als Verzeichnis bezeichnet. Hierbei handelt es sich um die Kopie, in der ein Benutzer tatsächlich Änderungen vornimmt. Es kann viele Arbeitskopien von einem bestimmten Projekt vorhanden sein. Jeder Entwickler hat in der Regel ein eigenes kopieren.

 Get eine Get-Vorgang bringt des Benutzers Arbeitskopie auf dem neuesten Stand mit der Kopie des Repositorys. Im Gegensatz zu einer ausgecheckten Element gehört wird ein Get ausgeführt, wenn der Benutzer einfach die aktuelle Kopie benötigt, aber keine Änderungen vornehmen will.

 Verlauf ist es in der Regel einen Überblick über alle Auschecken, Eincheckvorgänge, Updates, Tags und Versionen, die in den Quellcodeverwaltungs-Repository durchgeführt wird.

 IDE in der Regel verweist auf der Visual Studio integrierten Entwicklungsumgebung. Es kann jedoch auch andere Client-Umgebungen verweisen, die von der Quelle-Plug-in-API erkannt.

 Führen Sie den Prozess, bei der, den Quelle mindestens zwei Codedateien kombiniert werden, um eine neue Datei zu erstellen, die alle Funktionen von vorherigen-Dateien enthält. Dieses Konzept ist wichtig, in der Versionskontrolle arbeiten, in denen zwei oder mehr Entwickler gleichzeitig an Dateien.

 Projekt ein Quellcode-Verwaltungsordner wird häufig als Projekt bezeichnet. Dies muss keine Beziehung mit der Projekte oder Projektmappen in Visual Studio.

 -Plug-in eine DLL-Datei, die Quellcodeverwaltungsfunktionen bereitstellt, durch die Implementierung der Source-Plug-in-API.

 Repository die Masterkopie, in denen ein Quellcodeverwaltungssystem vollständige Revisionsverlauf des Projekts gespeichert. Jedes Projekt verfügt über genau ein Repository.

 Revision ein Commit Änderung in der Versionsgeschichte einer Datei oder eine Gruppe von Dateien. Eine Revision wird eine Momentaufnahme in einem Projekt auf kontinuierlich ändern.

## <a name="see-also"></a>Siehe auch
- [Quellcodeverwaltungs-Plug-Ins](../extensibility/source-control-plug-ins.md)