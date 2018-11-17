---
title: Automatisierung für Konfigurations- und SelectedItem-Objekte | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- automation [Visual Studio SDK], SelectedItem object
- automation [Visual Studio SDK], builds
ms.assetid: 120377f1-51aa-4445-b2f7-06ab7fc2b47f
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 612916da7922900a1054d785dad86ed448aa1f12
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51733471"
---
# <a name="automation-for-configuration-and-selecteditem-objects"></a>Automatisierung für Konfigurations- und SelectedItem-Objekte
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Sie können die Build- und das ausgewählte Element Prozesse in automatisieren [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
## <a name="automation-for-builds"></a>Automatisierung für Builds  
 Build- oder Konfiguration verfügt über ein Automatisierungsmodell, das bereitgestellt wird, bei der Implementierung <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider>. Weitere Informationen finden Sie unter [Grundlagen der Buildkonfiguration](../../ide/understanding-build-configurations.md).  
  
 Wenn Sie eine VSPackage zu erstellen und die Konfigurationsoptionen steuern möchten, müssen Sie das Automatisierungsmodell verwenden.  
  
## <a name="automation-for-selecteditem"></a>Automatisierung für SelectedItem  
 Sie müssen keine Geben Sie eine Implementierung für die `SelectedItem` Objekt, da Visual Studio eine Standardimplementierung enthält. Sie können jedoch implementieren das `SelectedItem` Objekt, falls gewünscht. Müssen Sie ein Objekt mit implementieren die `SelectedItem` -Schnittstelle und eine Antwort an einen Aufruf der <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> mit VSITEMID festgelegt ist, <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>   
 [Mitwirken am Automatisierungsmodell](../../extensibility/internals/contributing-to-the-automation-model.md)   
 [Grundlagen der Buildkonfiguration](../../ide/understanding-build-configurations.md)

