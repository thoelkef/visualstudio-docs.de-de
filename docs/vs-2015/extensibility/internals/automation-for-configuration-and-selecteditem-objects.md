---
title: Automatisierung für Konfigurations- und SelectedItem-Objekte | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
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
ms.openlocfilehash: f9d5da07c4505aef38fbef22b8680a8c0914056a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47512632"
---
# <a name="automation-for-configuration-and-selecteditem-objects"></a>Automatisierung für Konfigurations- und SelectedItem-Objekte
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Automatisierung für Konfigurations- und SelectedItem-Objekte](https://docs.microsoft.com/visualstudio/extensibility/internals/automation-for-configuration-and-selecteditem-objects).  
  
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

