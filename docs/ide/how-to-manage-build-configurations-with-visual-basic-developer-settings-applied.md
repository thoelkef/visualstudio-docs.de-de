---
title: 'Vorgehensweise: Verwalten von Buildkonfigurationen mit aktivierten Visual Basic Developer-Einstellungen | Microsoft-Dokumentation'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio, building with Visual Basic settings
- MSBuild, debug build
- advanced build configurations
- building with Visual Basic developer settings
- debug builds
- MSBuild, release build
- release builds
ms.assetid: eaea6e0b-6c61-4869-8d63-d372c745a23c
caps.latest.revision: "9"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3e61fb6667c16fd75cef78fbcaa835b97603dbe5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-manage-build-configurations-with-visual-basic-developer-settings-applied"></a>Gewusst wie: Verwalten von Buildkonfigurationen mit aktivierten Visual Basic Developer-Einstellungen
Standardmäßig werden alle Optionen für die Buildkonfiguration ausgeblendet, wenn die [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]-Developer-Einstellungen aktiviert sind. In diesem Thema wird erläutert, wie Sie diese Einstellungen manuell aktivieren.  
  
## <a name="enabling-advanced-build-configurations"></a>Aktivieren erweiterter Buildkonfigurationen  
 Standardmäßig blenden die [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]-Developer-Einstellungen die Option aus, das Dialogfeld **Konfigurations-Manager** und die Listen **Konfiguration** und **Plattform** im [Projekt-Designer](..//ide/reference/application-page-project-designer-visual-basic.md) zu öffnen.  
  
#### <a name="to-enable-advanced-build-configurations"></a>So aktivieren Sie erweiterte Buildkonfigurationen  
  
1.  Klicken Sie im Menü **Extras** auf **Optionen**.  
  
2.  Erweitern Sie **Projekte und Projektmappen**, und klicken Sie auf **Allgemein**.  
  
    > [!NOTE]
    >  Der Knoten **Allgemein** ist auch sichtbar, wenn die Option **Alle Einstellungen anzeigen** deaktiviert ist. Wenn Sie alle verfügbaren Optionen anzeigen möchten, klicken Sie auf **Alle Einstellungen anzeigen**.  
  
3.  Klicken Sie auf **Erweiterte Buildkonfigurationen anzeigen**.  
  
4.  Klicken Sie auf **OK**.  
  
     Der **Konfigurations-Manager** ist nun im Menü **Erstellen** verfügbar, und die Listen **Konfiguration** und **Plattform** werden im Projekt-Designer angezeigt.  
  
## <a name="see-also"></a>Siehe auch  
 [Grundlagen der Buildkonfiguration](../ide/understanding-build-configurations.md)   
 [Kompilieren und Erstellen](../ide/compiling-and-building-in-visual-studio.md)