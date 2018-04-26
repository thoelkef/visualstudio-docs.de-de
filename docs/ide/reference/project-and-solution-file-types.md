---
title: Projekt- und Projektmappen-Dateitypen
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- File Properties.CopyToOutputDirectory
- File Properties.CustomToolNamespace
- File Properties.FileName
- File Properties.FullPath
- File Properties.BuildAction
- File Properties.CustomTool
- FileProperties
helpviewer_keywords:
- .sln files
- .suo files
- file types [Visual Studio]
- file extensions [Visual Studio]
- solution files [Visual Studio]
- sln files
- suo files
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b3786d6f38e4f87aa05a51b0a6112613bda65e56
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="project-and-solution-file-types"></a>Projekt- und Projektmappen-Dateitypen

Visual Studio unterstützt eine Vielzahl von Dateitypen. In einer bestimmten Installation wird durch die installierten Komponenten ermittelt, welche Dateitypen unterstützt werden. In diesem Thema werden die Arten von Projektmappen und Projektdateitypen aufgeführt, die in typischen Installationen unterstützt werden.

## <a name="solution-files-sln-and-suo"></a>Projektmappendateien (.sln und .suo)

Visual Studio speichert die Einstellungen von Projektmappen in zwei Dateitypen (.sln und .suo). Diese Dateien, die allgemein als Projektmappendateien bezeichnet werden, enthalten alle Informationen, die vom Projektmappen-Explorer für die Anzeige einer grafischen Oberfläche zum Verwalten der Dateien benötigt werden.

|Erweiterung|name|description|
|---------------|----------|-----------------|
|.sln|Visual Studio-Projektmappe|Organisiert Projekte, Projektelemente und Projektmappenelemente in einer Projektmappe.|
|.suo|Benutzeroptionen bei Projektmappen|Damit können Sie die Anpassungen auf Benutzerebene verfolgen, die Sie in Visual Studio vorgenommen haben, z.B. Haltepunkte.|

## <a name="project-files"></a>Projektdateien

Projekte können viele verschiedene Dateitypen enthalten. Dateien mit C#-Code haben beispielsweise die Erweiterung **.cs**, und Dateien in C++ haben **.cpp**. Ressourcen werden in **RESX**-Dateien und XAML-Code in **XAML**-Dateien gespeichert. [App.config](../../ide/managing-application-settings-dotnet.md)-Dateien enthalten Informationen zur Anwendung, wie z.B. Verbindungszeichenfolgen, die nicht im Anwendungscode enthalten sein sollten.

Weitere Informationen zu Dateitypen in C++-Projekten finden Sie unter [Für Visual C++-Projekte erstellte Dateitypen](/cpp/ide/file-types-created-for-visual-cpp-projects).

## <a name="see-also"></a>Siehe auch

- [Projektmappen und Projekte](../../ide/solutions-and-projects-in-visual-studio.md)