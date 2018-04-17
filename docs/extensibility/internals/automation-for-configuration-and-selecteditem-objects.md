---
title: Automatisierung für die Konfiguration und "SelectedItem" Objekte | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], SelectedItem object
- automation [Visual Studio SDK], builds
ms.assetid: 120377f1-51aa-4445-b2f7-06ab7fc2b47f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4d4ac269664136aed51542e53900ffc1c87f21fe
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="automation-for-configuration-and-selecteditem-objects"></a>Automatisierung für die Konfiguration und "SelectedItem"-Objekte
Können automatisiert werden, die Build- und ausgewählte Element Prozesse in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="automation-for-builds"></a>Automatisierung für Builds  
 Erstellung oder Konfiguration verfügt über ein Automatisierungsmodell, das bereitgestellt wird, bei der Implementierung <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider>. Weitere Informationen finden Sie unter [Grundlagen der Buildkonfiguration](../../ide/understanding-build-configurations.md).  
  
 Wenn Sie eine VSPackage erstellen und Konfigurationsoptionen steuern möchten, müssen Sie das Automatisierungsmodell verwenden.  
  
## <a name="automation-for-selecteditem"></a>Automatisierung für "SelectedItem"  
 Sie müssen keine Geben Sie eine Implementierung für die `SelectedItem` Objekt, da Visual Studio eine standard-Implementierung enthält. Sie können jedoch implementieren die `SelectedItem` Objekt, falls gewünscht. Müssen Sie ein Objekt, das enthält implementieren die `SelectedItem` -Schnittstelle und eine Antwort auf einen Aufruf der <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> mit VSITEMID festgelegt ist, <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>   
 [Das Automatisierungsmodell beitragen.](../../extensibility/internals/contributing-to-the-automation-model.md)   
 [Grundlagen der Buildkonfiguration](../../ide/understanding-build-configurations.md)