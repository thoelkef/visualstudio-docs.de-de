---
title: Automatisierung für Konfigurations- und SelectedItem-Objekte | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], SelectedItem object
- automation [Visual Studio SDK], builds
ms.assetid: 120377f1-51aa-4445-b2f7-06ab7fc2b47f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1ee4bcddd7c23f5178984c2c76b059209a965956
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62910630"
---
# <a name="automation-for-configuration-and-selecteditem-objects"></a>Automatisierung für Konfigurations- und SelectedItem-Objekte

Sie können die Build- und das ausgewählte Element Prozesse in Visual Studio automatisieren.

## <a name="automation-for-builds"></a>Automatisierung für builds

Build- oder Konfiguration verfügt über ein Automatisierungsmodell, das bereitgestellt wird, bei der Implementierung <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider>. Weitere Informationen finden Sie unter [Grundlagen der Buildkonfigurationen](../../ide/understanding-build-configurations.md).

Wenn Sie eine VSPackage zu erstellen und die Konfigurationsoptionen steuern möchten, müssen Sie das Automatisierungsmodell verwenden.

## <a name="automation-for-selecteditem"></a>Automatisierung für SelectedItem

Sie müssen keine Geben Sie eine Implementierung für die `SelectedItem` Objekt, da Visual Studio eine Standardimplementierung enthält. Sie können jedoch implementieren das `SelectedItem` Objekt, falls gewünscht. Müssen Sie ein Objekt mit implementieren die `SelectedItem` -Schnittstelle und eine Antwort an einen Aufruf der <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> -Methode mit `VSITEMID` festgelegt [__VSHPROPID. VSHPROPID_ExtSelectedItem](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_ExtSelectedItem>).

## <a name="see-also"></a>Siehe auch

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>
- [Mitwirken Sie am Automatisierungsmodell](../../extensibility/internals/contributing-to-the-automation-model.md)
- [Grundlagen der Buildkonfiguration](../../ide/understanding-build-configurations.md)