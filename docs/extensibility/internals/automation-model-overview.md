---
title: Übersicht über das Automatisierungsmodell | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], about automation
- extensibility
ms.assetid: 12b6d6db-0d22-4aaa-aa7d-1365f759b7b0
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 42b1237825eaa3fe2dec9ffa0142b78bc4693976
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66326314"
---
# <a name="automation-model-overview"></a>Übersicht über das Automatisierungsmodell
Das Automatisierungsmodell besteht aus einem Satz von Objekten, die mit denen Sie ein Visual Studio-add-in oder eine Erweiterung schreiben können. Ein Add-in ist eine Anwendung, die Visual Studio-Umgebung bearbeiten kann, und Automatisieren allgemeiner Aufgaben. Visual Studio-Erweiterung kann Erstellen von benutzerdefinierten Komponenten für Visual Studio oder die Funktionalität des standard-Komponenten wie z. B. den Text-Editor hinzufügen.

## <a name="objects-in-the-automation-model"></a>Objekte im Automatisierungsmodell
 Das Automatisierungsmodell bestehen aus miteinander verbundene Gruppen von Objekten, die wesentliche Merkmale der gemeinsamen Umgebung zu steuern. Das folgende Diagramm zeigt den umfangreichen Satz von Visual Studio-Objekten, aus denen das Automatisierungsmodell.

 ![Diagramm des Visual Studio-Automatisierung](../../extensibility/internals/media/vsvisualstudioautomationobjectchart.gif "VsVisualStudioAutomationObjectChart")

 Weitere Informationen finden Sie unter [Erweitern von Visual Studio-Umgebung](https://msdn.microsoft.com/Library/4173a963-7ac7-4966-9bb7-e28a9d9f6792).

 Die Umgebung bietet ein Modell für verschiedene Funktionsbereiche. Es ist z. B. ein Codemodell für verschiedene Elemente, die Sie ggf. im Code finden. Es gibt ein Dokumentmodell für die verschiedenen Elemente des Dokuments. Ein Bereich, der Projektbereich ist von besonderem Interesse für VSPackage-Anbieter. Möchten Sie wahrscheinlich Ihre neue Projekttypen mitwirken am Automatisierungsmodell in die gleiche Weise wie [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] und [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] zum Automatisierungsmodell beitragen. Dass der Prozess in beschriebene [Bereitstellen von Automatisierung für VSPackages](../../extensibility/internals/providing-automation-for-vspackages.md).

 Stellen, in dem Sie die Erweitern des Automatisierungsmodells der Umgebung berücksichtigen können:

- Projekt

- Dokument

- Code

- Build

Weitere Informationen zu Automation finden Sie unter [Automatisierung und Erweiterbarkeit für Visual Studio](../extensibility-in-visual-studio.md). In diesem Dokument und die Dokumente wird Links, um Ihnen zu treffen von Entscheidungen in Bezug auf, wie Sie Automation für das VSPackage bereitgestellt werden sollen.

## <a name="see-also"></a>Siehe auch
- [Vorgehensweise: Erstellen Sie ein Add-in](https://msdn.microsoft.com/Library/50be56d2-e3a5-4cd2-8569-2a0666b268ce)