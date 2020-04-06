---
title: Quellcodeverwaltung Plug-in Glossar | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- glossary [Visual Studio SDK]
- source control plug-ins, glossary
ms.assetid: f224bbc9-38fc-4c80-ab09-51dcc8969f8e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3835561eb63fa2a4a71174732c07ecd73f1df5d7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699908"
---
# <a name="source-control-plug-in-glossary"></a>Glossar für das Quellcodeverwaltungs-Plug-In
Die folgenden hilfreichen Begriffe und Definitionen beziehen sich auf die Dokumentation des Source Control Plug-In SDK.

## <a name="definitions"></a>Definitionen
 Einchecken Wenn ein Benutzer Änderungen an einer Arbeitskopie vornimmt, muss ein Benutzer Änderungen aus der Arbeitskopie an das zentrale Quellcodeverwaltungsrepository senden. Dadurch wird eine neue Revision der Datei erstellt, die anderen Benutzern zur Verfügung steht. Dieser Prozess wird als Einchecken bezeichnet.

 Auschecken Der Vorgang, bei dem eine Arbeitskopie aus dem Repository angefordert wird, und informiert das Repository über Ihre Absicht, sie zu ändern. Eine Arbeitskopie gibt den Stand des Projekts zum Zeitpunkt des Auscheckens wieder.

 Client Ein Programm, das das Quellcodeverwaltungssystem verwendet. Für die Zwecke dieser Dokumentation ist es die Visual Studio-IDE.

 Kommentar Eine Meldung, die die Änderungen beschreibt, die ein Benutzer an eine Revision anfügen kann, wenn ein Quellcodeverwaltungsvorgang ausgeführt wird.

 Konflikt Eine Situation, in der zwei Benutzer versuchen, Änderungen an derselben Region derselben Datei einzuchecken. In der Regel muss eine Zusammenführung durchgeführt werden.

 Verzeichnis Ein clientseitig lokaler Ordner wird als Verzeichnis bezeichnet. Dies ist die Kopie, in der ein Benutzer tatsächlich Änderungen vornimmt. Es können viele Arbeitskopien eines bestimmten Projekts vorhanden sein; in der Regel hat jeder Entwickler seine eigene Kopie.

 Abrufen Ein Absicherungsvorgang bringt die Arbeitskopie des Benutzers mit der Repository-Kopie auf den neuesten Stand. Im Gegensatz zum Auschecken wird ein Get durchgeführt, wenn der Benutzer einfach die neueste Kopie benötigt, aber keine Änderungen vornehmen möchte.

 Historie Es ist in der Regel eine Zusammenfassung aller Auscheckvorgänge, Eincheckvorgänge, Updates, Tags und Releases, die im Quellcodeverwaltungs-Repository durchgeführt werden.

 IDE bezieht sich im Allgemeinen auf die integrierte Visual Studio-Entwicklungsumgebung. Es könnte sich jedoch auch auf andere Clientumgebungen beziehen, die die Quellcodeverwaltungs-Plug-In-API erkennen.

 Zusammenführen Der Prozess, bei dem zwei oder mehr Quellcodedateien zu einer neuen Datei kombiniert werden, die alle Features aus früheren Dateien enthält. Dieses Konzept ist bei der Versionskontrolle von entscheidender Bedeutung, wenn zwei oder mehr Entwickler gleichzeitig an Dateien arbeiten.

 Projekt Ein Quellcodeverwaltungsordner wird häufig als Projekt bezeichnet. Dies hat keine Beziehung zu Projekten oder Projektlösungen in Visual Studio.

 Plug-In-DLL, die Quellcodeverwaltungsfunktionen durch Implementieren der Quellcodeverwaltungs-Plug-In-API bereitstellt.

 Repository Die Masterkopie, in der ein Quellcodeverwaltungssystem den vollständigen Revisionsverlauf eines Projekts speichert. Jedes Projekt verfügt über genau ein Repository.

 Revision Eine festgeschriebene Änderung im Verlauf einer Datei oder eines Satzes von Dateien. Eine Revision ist eine Momentaufnahme in einem sich ständig ändernden Projekt.

## <a name="see-also"></a>Weitere Informationen
- [Quellcodeverwaltungs-Plug-Ins](../extensibility/source-control-plug-ins.md)
