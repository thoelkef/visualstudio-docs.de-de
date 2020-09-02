---
title: 'Vorgehensweise: Verwalten von Buildkonfigurationen mit aktivierten Visual Basic Developer-Einstellungen | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
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
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a5f8568edc636955558ec93b55c0aedebf0065d3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651835"
---
# <a name="how-to-manage-build-configurations-with-visual-basic-developer-settings-applied"></a>Gewusst wie: Verwalten von Buildkonfigurationen mit aktivierten Visual Basic Developer-Einstellungen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Standardmäßig werden alle Optionen für die Buildkonfiguration ausgeblendet, wenn die [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]-Developer-Einstellungen aktiviert sind. In diesem Thema wird erläutert, wie Sie diese Einstellungen manuell aktivieren.

## <a name="enabling-advanced-build-configurations"></a>Aktivieren erweiterter Buildkonfigurationen
 Standardmäßig blenden die [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]-Developer-Einstellungen die Option aus, das Dialogfeld **Konfigurations-Manager** und die Listen **Konfiguration** und **Plattform** im [Projekt-Designer](https://msdn.microsoft.com/898dd854-c98d-430c-ba1b-a913ce3c73d7) zu öffnen.

#### <a name="to-enable-advanced-build-configurations"></a>So aktivieren Sie erweiterte Buildkonfigurationen

1. Klicken Sie im Menü **Extras** auf **Optionen**.

2. Erweitern Sie **Projekte und Projektmappen**, und klicken Sie auf **Allgemein**.

    > [!NOTE]
    > Der Knoten **Allgemein** ist auch sichtbar, wenn die Option **Alle Einstellungen anzeigen** deaktiviert ist. Wenn Sie alle verfügbaren Optionen anzeigen möchten, klicken Sie auf **Alle Einstellungen anzeigen**.

3. Klicken Sie auf **Erweiterte Buildkonfigurationen anzeigen**.

4. Klicken Sie auf **OK**.

     Der **Konfigurations-Manager** ist nun im Menü **Erstellen** verfügbar, und die Listen **Konfiguration** und **Plattform** werden im Projekt-Designer angezeigt.

## <a name="see-also"></a>Weitere Informationen
 Grundlegendes zu [Build-Konfigurationen](../ide/understanding-build-configurations.md) [Kompilieren und](../ide/compiling-and-building-in-visual-studio.md) erstellen
