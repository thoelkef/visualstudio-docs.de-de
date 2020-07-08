---
title: Quellcodeverwaltung
description: Verwenden von Git und Subversion in Visual Studio für Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.assetid: 49917483-28AA-4598-A847-71F1F2E0DCB5
ms.topic: overview
ms.openlocfilehash: 33fdfe3ef6d292dded34a3b468ed9d60d0f6c318
ms.sourcegitcommit: 2ce59c2ffeba5ba7f628c2e6c75cba4731deef8a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2020
ms.locfileid: "85938427"
---
# <a name="version-control"></a>Versionskontrolle

Versionskontrolle ist ein System zum Verwalten von Dateien in vielen verschiedenen Versionen, und in der Softwareentwicklung tragen im Allgemeinen viele Entwickler dazu bei. Der Hauptzweck eines Versionskontrollsystems (Version Control System, _VCS_) besteht darin, eine Lösung zu finden, sodass alle Benutzer gleichzeitig an der CodeBase arbeiten können.

Den Kern eines jeden Versionskontrollsystems ist ein _Repository_, das als zentraler Datenspeicher für alle verschiedenen Dateien fungiert, wie ein Dateiserver. Im Gegensatz zu einem Dateiserver enthält das Repository jedoch den gesamten Verlauf des Projekts und alle Änderungen, die vorgenommen wurden.

Wenn das Repository also der zentrale Datenspeicher ist, hat jeder Benutzer logischerweise einen lokalen Datenspeicher, sodass er an einem Projekt arbeiten kann. Hierbei spricht man von einer _Arbeitskopie_. In Visual Studio für Mac wird Ihre Arbeitskopie ebenso wie alle anderen lokalen Verzeichnisse auf dem Computer angezeigt. So können Sie in diesen Dateien lesen schreiben. Da Visual Studio für Mac aber in ein Versionskontrollsystem integriert ist, können Sie Subversion und Git nutzen, ohne die IDE zu verlassen.

Subversion ist ein zentralisiertes Versionskontrollsystem, was bedeutet, dass ein einzelner Server alle Dateien und Revisionen enthält, aus denen Benutzer eine beliebige Version einer beliebigen Datei auschecken können. Wenn Dateien aus einem Remoterepository von Subversion ausgecheckt werden, erhalten Benutzer eine Momentaufnahme des Repositorys.

Bei Git handelt es sich um ein verteiltes Versionskontrollsystem, mit dem die Mitglieder eines Teams gleichzeitig an den gleichen Dokumenten arbeiten können. Bei Git kann ein einzelner Server alle Dateien enthalten. Wenn aber ein Repository aus dieser zentralen Quelle ausgecheckt wird, wird das gesamte Repository auf Ihrem Computer lokal geklont.

## <a name="basic-concepts"></a>Grundlegende Konzepte

Visual Studio für Mac bietet Unterstützung für beide Versionskontrollsysteme von Git und Subversion. In den folgenden Artikeln werden das Einrichten von Git- und Subversion-Repositorys über Visual Studio für Mac sowie einfache Funktionen wie das Überprüfen, Committen und Pushen von Änderungen erläutert.

* [Setting Up a Git Repository (Einrichten eines Git-Repository)](set-up-git-repository.md)
* [Working with Git (Arbeiten mit Git)](working-with-git.md)
* [Setting Up a Subversion Repository (Einrichten eines Subversion-Repository)](set-up-subversion-repository.md)
* [Working with Subversion (Arbeiten mit Subversion)](working-with-subversion.md)

## <a name="see-also"></a>Siehe auch

* [Versionskontrolle in Visual Studio (unter Windows)](/visualstudio/version-control/)