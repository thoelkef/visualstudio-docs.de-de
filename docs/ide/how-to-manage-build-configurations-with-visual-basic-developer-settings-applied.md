---
title: 'Vorgehensweise: Verwalten von Buildkonfigurationen mit aktivierten Visual Basic Developer-Einstellungen'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-compile
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, building with Visual Basic settings
- MSBuild, debug build
- advanced build configurations
- building with Visual Basic developer settings
- debug builds
- MSBuild, release build
- release builds
ms.assetid: eaea6e0b-6c61-4869-8d63-d372c745a23c
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 987419e62d54b44a21a70f625e2a240bd7aecc21
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
ms.locfileid: "31946259"
---
# <a name="how-to-manage-build-configurations-with-visual-basic-developer-settings-applied"></a>Vorgehensweise: Verwalten von Buildkonfigurationen mit aktivierten Visual Basic Developer-Einstellungen

Standardmäßig werden alle Optionen für die Buildkonfiguration ausgeblendet, wenn die Visual Basic-Entwicklereinstellungen aktiviert sind. In diesem Thema wird erläutert, wie Sie diese Einstellungen manuell aktivieren.

## <a name="enable-advanced-build-configurations"></a>Aktivieren von erweiterten Buildkonfigurationen

Standardmäßig blenden die Visual Basic-Entwicklereinstellungen die Option aus, das Dialogfeld **Konfigurations-Manager** und die Listen **Konfiguration** und **Plattform** im [Projekt-Designer](..//ide/reference/application-page-project-designer-visual-basic.md) zu öffnen.

1.  Klicken Sie im Menü **Extras** auf **Optionen**.

2.  Erweitern Sie **Projekte und Projektmappen**, und klicken Sie auf **Allgemein**.

    > [!NOTE]
    > Der Knoten **Allgemein** ist auch sichtbar, wenn die Option **Alle Einstellungen anzeigen** deaktiviert ist. Wenn Sie alle verfügbaren Optionen anzeigen möchten, klicken Sie auf **Alle Einstellungen anzeigen**.

3.  Klicken Sie auf **Erweiterte Buildkonfigurationen anzeigen**.

4.  Klicken Sie auf **OK**.

     Der **Konfigurations-Manager** ist nun im Menü **Erstellen** verfügbar, und die Listen **Konfiguration** und **Plattform** werden im **Projekt-Designer** angezeigt.

## <a name="see-also"></a>Siehe auch

- [Grundlagen der Buildkonfiguration](../ide/understanding-build-configurations.md)
- [Kompilieren und Erstellen](../ide/compiling-and-building-in-visual-studio.md)