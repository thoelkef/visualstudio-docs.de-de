---
title: Quellcodeverwaltung
description: "Verwenden von Git und Subversion in Visual Studio für Mac"
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: 49917483-28AA-4598-A847-71F1F2E0DCB5
ms.translationtype: HT
ms.sourcegitcommit: e2b7ff9126e1cc38ac2e58d6be339b656a024e7f
ms.openlocfilehash: a63ebdccc2a7cbde18715291a65ada613dc2c00e
ms.contentlocale: de-de
ms.lasthandoff: 08/11/2017

---

# <a name="version-control"></a>Versionskontrolle

Versionskontrolle ist ein System zum Verwalten von Dateien in vielen verschiedenen Versionen, und in der Softwareentwicklung tragen im Allgemeinen viele Entwickler dazu bei. Der Hauptzweck eines Versionskontrollsystems (Version Control System, _VCS_) besteht darin, eine Lösung zu finden, sodass alle Benutzer gleichzeitig an der CodeBase arbeiten können.

Den Kern eines jeden Versionskontrollsystems ist ein _Repository_, das als zentraler Datenspeicher für alle verschiedenen Dateien fungiert, wie ein Dateiserver. Im Gegensatz zu einem Dateiserver enthält das Repository jedoch den gesamten Verlauf des Projekts und alle Änderungen, die vorgenommen wurden.

Wenn das Repository also der zentrale Datenspeicher ist, hat jeder Benutzer logischerweise einen lokalen Datenspeicher, sodass er an einem Projekt arbeiten kann. Hierbei spricht man von einer _Arbeitskopie_. In Visual Studio für Mac wird Ihre Arbeitskopie ebenso wie alle anderen lokalen Verzeichnisse auf dem Computer angezeigt. So können Sie in diesen Dateien lesen schreiben. Da in Visual Studio für Mac aber in eine Versionskontrollsystem integriert ist, können Sie die Leistungsfähigkeit von Subversion und Git nutzen, ohne die IDE zu verlassen.

Subversion ist ein zentralisiertes Versionskontrollsystem. Dies bedeutet, dass ein einzelner Server alle Dateien und Reversionen enthält, aus denen Benutzer eine beliebige Version einer beliebigen Datei auschecken können. Wenn Dateien aus einem Remoterepository von Subversion ausgecheckt werden, erhalten Benutzer zu diesem Zeitpunkt eine Momentaufnahme des Repositorys.

Bei Git handelt es sich um ein verteiltes Versionskontrollsystem, mit dem die Mitglieder eines Teams gleichzeitig an den gleichen Dokumenten arbeiten können. Dies bedeutet, dass es einen einzelnen Server mit allen Dateien geben kann. Wenn aber ein Repository aus dieser zentralen Quelle ausgecheckt wird, wird das gesamte Repository auf Ihrem Computer lokal geklont.

# <a name="basic-concepts"></a>Grundlegende Konzepte 

Visual Studio für Mac bietet Unterstützung für beide Versionskontrollsysteme von Git und Subversion. Die unten verlinkten Handbüchern erläutern das Einrichten von Git- und Subversion-Repositorys über Visual Studio für Mac sowie einfache Funktionen wie das Überprüfen, das Ausführen eines Commits und das Übertragen von Änderungen.

* [Setting Up a Git Repository (Einrichten eines Git-Repository)](~/set-up-git-repository.md) 
* [Working with Git (Arbeiten mit Git)](~/working-with-git.md)
* [Setting Up a Subversion Repository (Einrichten eines Subversion-Repository)](~/set-up-subversion-repository.md)
* [Working with Subversion (Arbeiten mit Subversion)](~/working-with-subversion.md)
