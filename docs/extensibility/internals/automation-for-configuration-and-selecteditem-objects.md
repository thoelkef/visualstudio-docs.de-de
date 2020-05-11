---
title: Automatisierung für Konfiguration und SelectedItem-Objekte | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], SelectedItem object
- automation [Visual Studio SDK], builds
ms.assetid: 120377f1-51aa-4445-b2f7-06ab7fc2b47f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0341cdf56b32b8b1ac77104b3f3e813ae0610767
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709968"
---
# <a name="automation-for-configuration-and-selecteditem-objects"></a>Automatisierung für Konfiguration und SelectedItem-Objekte

Sie können die Build- und ausgewählten Elementprozesse in Visual Studio automatisieren.

## <a name="automation-for-builds"></a>Automatisierung für Builds

Beim Erstellen oder Erstellen verfügt die Konfiguration <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider>über ein Automatisierungsmodell, das beim Implementieren bereitgestellt wird. Weitere Informationen finden Sie unter [Grundlagen der Buildkonfigurationen](../../ide/understanding-build-configurations.md).

Wenn Sie ein VSPackage erstellen und Konfigurationsoptionen steuern möchten, müssen Sie das Automatisierungsmodell verwenden.

## <a name="automation-for-selecteditem"></a>Automatisierung für SelectedItem

Sie müssen keine Implementierung für `SelectedItem` das Objekt bereitstellen, da Visual Studio eine Standardimplementierung enthält. Sie können das `SelectedItem` Objekt jedoch implementieren, wenn Sie es vorziehen. Sie müssen ein Objekt `SelectedItem` implementieren, das die Schnittstelle enthält, `VSITEMID` und eine Antwort auf einen Aufruf an die Methode zurückgeben, der <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> auf __VSHPROPID festgelegt [ist. VSHPROPID_ExtSelectedItem](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_ExtSelectedItem>).

## <a name="see-also"></a>Weitere Informationen

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>
- [Beitrag zum Automatisierungsmodell](../../extensibility/internals/contributing-to-the-automation-model.md)
- [Grundlagen der Buildkonfiguration](../../ide/understanding-build-configurations.md)
