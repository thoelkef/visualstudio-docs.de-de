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
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 90af8e941eb18a703974859ea4393fd84182077d
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53905649"
---
# <a name="automation-for-configuration-and-selecteditem-objects"></a>Automatisierung für Konfigurations- und SelectedItem-Objekte
Sie können die Build- und das ausgewählte Element Prozesse in automatisieren [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="automation-for-builds"></a>Automatisierung für builds  
 Build- oder Konfiguration verfügt über ein Automatisierungsmodell, das bereitgestellt wird, bei der Implementierung <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider>. Weitere Informationen finden Sie unter [Grundlagen der Buildkonfigurationen](../../ide/understanding-build-configurations.md).  
  
 Wenn Sie eine VSPackage zu erstellen und die Konfigurationsoptionen steuern möchten, müssen Sie das Automatisierungsmodell verwenden.  
  
## <a name="automation-for-selecteditem"></a>Automatisierung für SelectedItem  
 Sie müssen keine Geben Sie eine Implementierung für die `SelectedItem` Objekt, da Visual Studio eine Standardimplementierung enthält. Sie können jedoch implementieren das `SelectedItem` Objekt, falls gewünscht. Müssen Sie ein Objekt mit implementieren die `SelectedItem` -Schnittstelle und eine Antwort an einen Aufruf der <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> -Methode mit `VSITEMID` festgelegt <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>   
 [Mitwirken Sie am Automatisierungsmodell](../../extensibility/internals/contributing-to-the-automation-model.md)   
 [Grundlagen der Buildkonfiguration](../../ide/understanding-build-configurations.md)