---
title: Übersicht über automatisierungsmodell | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], about automation
- extensibility
ms.assetid: 12b6d6db-0d22-4aaa-aa7d-1365f759b7b0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7b940677c370106ebdcc63c7984d553003251e8a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710006"
---
# <a name="automation-model-overview"></a>Übersicht über das Automatisierungsmodell
Das Automatisierungsmodell besteht aus einer Gruppe von Objekten, für die Sie ein Visual Studio-Add-In oder eine Erweiterung schreiben können. Ein Add-In ist eine Anwendung, die die Visual Studio-Umgebung bearbeiten und allgemeine Aufgaben automatisieren kann. Eine Visual Studio-Erweiterung kann benutzerdefinierte Visual Studio-Komponenten erstellen oder der Funktionalität von Standardkomponenten wie dem Texteditor hinzufügen.

## <a name="objects-in-the-automation-model"></a>Objekte im Automatisierungsmodell
 Das Automatisierungsmodell besteht aus verwandten Gruppen von Objekten, die wichtige Facetten der gemeinsamen Umgebung steuern. Das folgende Diagramm zeigt den umfangreichen Satz von Visual Studio-Objekten, aus denen das Automatisierungsmodell besteht.

 ![Visual Studio-Automatisierungsobjektdiagramm](../../extensibility/internals/media/vsvisualstudioautomationobjectchart.gif "vsVisualStudioAutomationObjectChart")

 Weitere Informationen finden Sie unter [Erweitern der Visual Studio-Umgebung](https://msdn.microsoft.com/Library/4173a963-7ac7-4966-9bb7-e28a9d9f6792).

 Die Umgebung bietet ein Modell für verschiedene Funktionsbereiche. Beispielsweise gibt es ein Codemodell für verschiedene Elemente, die Sie möglicherweise im Code finden. Es gibt ein Dokumentmodell für verschiedene Dokumentelemente. Ein Bereich, der Projektbereich, ist für VSPackage-Anbieter von besonderem Interesse. Sie möchten wahrscheinlich, dass Ihre neuen Projekttypen in etwa [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] genauso [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] zum Automatisierungsmodell beitragen wie zum Automatisierungsmodell. Dieser Prozess wird unter Bereitstellen der [Automatisierung für VSPackages](../../extensibility/internals/providing-automation-for-vspackages.md)beschrieben.

 Orte, an denen Sie das Automatisierungsmodell der Umgebung erweitern können:

- Project

- Dokument

- Code

- Build

Weitere Informationen zur Automatisierung finden Sie unter [Automatisierung und Erweiterbarkeit für Visual Studio](/visualstudio/extensibility/extensibility-in-visual-studio?view=vs-2015). Dieses Dokument und die Dokumente, zu denen es Links enthält, helfen Ihnen, Entscheidungen darüber zu treffen, wie Sie die Automatisierung Für Ihr VSPackage bereitstellen sollten.

## <a name="see-also"></a>Weitere Informationen
- [Gewusst wie: Erstellen eines Add-Ins](https://msdn.microsoft.com/Library/50be56d2-e3a5-4cd2-8569-2a0666b268ce)
