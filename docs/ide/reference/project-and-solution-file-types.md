---
title: Projekt- und Projektmappen-Dateitypen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology: vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: d239a5e129f12c4521ba190674d84430f8f2e646
ms.sourcegitcommit: 768118d470da9c7164d2f23ca918dfe26a4be72f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/28/2018
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

[Projektmappen und Projekte](../../ide/solutions-and-projects-in-visual-studio.md)