---
title: Übersicht über das Automatisierungs Modell | Microsoft-Dokumentation
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
ms.openlocfilehash: 6ea38dc79bd557f17bbae8276dd112304c9a40fa
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2019
ms.locfileid: "73186736"
---
# <a name="automation-model-overview"></a>Übersicht über das Automatisierungs Modell
Das Automatisierungs Modell besteht aus einem Satz von Objekten, für die Sie ein Visual Studio-Add-in oder eine Erweiterung schreiben können. Ein Add-in ist eine Anwendung, die die Visual Studio-Umgebung bearbeiten und häufige Aufgaben automatisieren kann. Mit einer Visual Studio-Erweiterung können benutzerdefinierte Visual Studio-Komponenten erstellt oder der Funktionalität von Standardkomponenten wie dem Text-Editor hinzugefügt werden.

## <a name="objects-in-the-automation-model"></a>Objekte im Automatisierungs Modell
 Das Automatisierungs Modell besteht aus verwandten Gruppen von Objekten, die die wichtigsten Facetten der allgemeinen Umgebung steuern. Das folgende Diagramm zeigt den umfangreichen Satz von Visual Studio-Objekten, die das Automatisierungs Modell bilden.

 ![Visual Studio-Automatisierungs Objekt Diagramm](../../extensibility/internals/media/vsvisualstudioautomationobjectchart.gif "vsvisualstudioautomationobjectchart")

 Weitere Informationen finden Sie unter [Erweitern der Visual Studio-Umgebung](https://msdn.microsoft.com/Library/4173a963-7ac7-4966-9bb7-e28a9d9f6792).

 Die Umgebung stellt ein Modell für unterschiedliche Funktionsbereiche bereit. Beispielsweise gibt es ein Code Modell für verschiedene Elemente, die möglicherweise im Code gefunden werden. Es ist ein Dokument Modell für verschiedene Dokument Elemente vorhanden. Ein Bereich, der Projektbereich, ist von besonderem Interesse für VSPackage-Anbieter. Wahrscheinlich möchten Sie, dass Ihre neuen Projekttypen auf die gleiche Weise wie [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] und [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] zum Automatisierungs Modell beitragen. Dieser Vorgang ist unter [Bereitstellen der Automatisierung für VSPackages](../../extensibility/internals/providing-automation-for-vspackages.md)beschrieben.

 Orte, an denen Sie in Erwägung gezogen werden, das Automatisierungs Modell der Umgebung zu erweitern:

- Projekt

- Dokument

- Code

- Build

Weitere Informationen zur Automatisierung finden Sie unter [Automatisierung und Erweiterbarkeit für Visual Studio](/visualstudio/extensibility/extensibility-in-visual-studio?view=vs-2015). Dieses Dokument und die Dokumente, zu denen es Links enthält, helfen Ihnen, Entscheidungen darüber zu treffen, wie Sie Automation für Ihr VSPackage bereitstellen sollten.

## <a name="see-also"></a>Siehe auch
- [Vorgehensweise: Erstellen eines Add-ins](https://msdn.microsoft.com/Library/50be56d2-e3a5-4cd2-8569-2a0666b268ce)