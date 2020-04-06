---
title: Eigenschaften Fenster-Schaltflächen | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, buttons
ms.assetid: bdd2e3a7-ae6e-4e88-be1a-e0e3b7ddbbcc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aaa4db159ccb0ecf3d0e9c9243e23fcd0dacc455
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706175"
---
# <a name="properties-window-buttons"></a>Schaltflächen des Eigenschaftenfensters
Abhängig von der Entwicklungssprache und dem Produkttyp werden bestimmte Schaltflächen standardmäßig auf der Symbolleiste für das **Eigenschaftenfenster** angezeigt. In allen Fällen werden die Schaltflächen **Categorized**, **Alphabetized**, **Properties**und **Property Pages** angezeigt. In Visual C- und Visual Basic wird auch die Schaltfläche **Ereignisse** angezeigt. In bestimmten Visual C++-Projekten werden die **Schaltflächen VC++ Messages** und **VC Overrides** angezeigt. Für andere Projekttypen werden möglicherweise zusätzliche Schaltflächen angezeigt. Weitere Informationen zu Schaltflächen im **Eigenschaftenfenster** finden Sie unter [Eigenschaftenfenster](../../ide/reference/properties-window.md).

## <a name="implementation-of-properties-window-buttons"></a>Implementierung von Eigenschaftenfensterschaltflächen
 Wenn Sie auf die Schaltfläche **Kategorisiert** klicken, ruft Visual Studio die <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties> Schnittstelle für das Objekt auf, das den Fokus hat, um seine Eigenschaften nach Kategorie zu sortieren. <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties>wird für `IDispatch` das Objekt implementiert, das im **Eigenschaftenfenster** angezeigt wird.

 Es gibt 11 vordefinierte Eigenschaftskategorien, die negative Werte haben. Sie können benutzerdefinierte Kategorien definieren, aber wir empfehlen, ihnen positive Werte zuzuweisen, um sie von den vordefinierten Kategorien zu unterscheiden.

 Die <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties.MapPropertyToCategory%2A> Methode gibt den entsprechenden Eigenschaftskategoriewert für die angegebene Eigenschaft zurück. Die <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties.GetCategoryName%2A> Methode gibt eine Zeichenfolge zurück, die den Kategorienamen enthält. Sie müssen nur Unterstützung für benutzerdefinierte Kategoriewerte bereitstellen, da Visual Studio die Standardeigenschaftskategoriewerte kennt.

 Wenn Sie auf die Schaltfläche **Alphabetisiert** klicken, werden die Eigenschaften in alphabetischer Reihenfolge nach Namen angezeigt. Die Namen werden `IDispatch` nach einem lokalisierten Sortieralgorithmus abgerufen.

 Wenn das **Eigenschaftenfenster** geöffnet ist, wird die **Schaltfläche Eigenschaften** automatisch als ausgewählt angezeigt. In anderen Teilen der Umgebung wird dieselbe Schaltfläche angezeigt, auf die Sie klicken können, um das **Eigenschaftenfenster** anzuzeigen.

 Die Schaltfläche **Eigenschaftenseiten** `ISpecifyPropertyPages` ist nicht verfügbar, wenn sie nicht für das ausgewählte Objekt implementiert ist. Eigenschaftenseiten zeigen konfigurationsabhängige Eigenschaften an, die in der Regel Projektlösungen und Projekten zugeordnet sind, aber auch Projektelementen zugeordnet werden können (z. B. in Visual C++).

> [!NOTE]
> Sie können dem **Eigenschaftenfenster** keine Symbolleistenschaltflächen hinzufügen, indem Sie nicht verwalteten Code verwenden. Um eine Symbolleistenschaltfläche hinzuzufügen, müssen Sie ein verwaltetes Objekt erstellen, das von abstammt. <xref:System.Windows.Forms.Design.PropertyTab>

## <a name="see-also"></a>Weitere Informationen
- [Erweitern von Eigenschaften](../../extensibility/internals/extending-properties.md)
