---
title: Automatisierung für Konfigurations-und SelectedItem-Objekte | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], SelectedItem object
- automation [Visual Studio SDK], builds
ms.assetid: 120377f1-51aa-4445-b2f7-06ab7fc2b47f
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 42faf8127c1ab70d3470aa497a0cdab6058060f8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157258"
---
# <a name="automation-for-configuration-and-selecteditem-objects"></a>Automatisierung für Konfigurations- und SelectedItem-Objekte
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Sie können die Prozesse Build und ausgewähltes Element in automatisieren [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
## <a name="automation-for-builds"></a>Automatisierung für Builds  
 Build oder Konfiguration verfügt über ein Automatisierungs Modell, das bei der Implementierung von bereitgestellt wird <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider> . Weitere Informationen finden Sie unter [Grundlagen der Buildkonfiguration](../../ide/understanding-build-configurations.md).  
  
 Wenn Sie ein VSPackage erstellen und Konfigurationsoptionen steuern möchten, müssen Sie das Automatisierungs Modell verwenden.  
  
## <a name="automation-for-selecteditem"></a>Automatisierung für SelectedItem  
 Sie müssen keine Implementierung für das-Objekt bereitstellen, `SelectedItem` da Visual Studio eine Standard Implementierung enthält. Es ist jedoch möglich, das-Objekt zu implementieren, `SelectedItem` Wenn Sie dies bevorzugen. Sie müssen ein-Objekt implementieren, das die `SelectedItem` -Schnittstelle enthält, und eine Antwort auf einen aufgerufen wird, wenn <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> vsitemid auf festgelegt ist <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> .  
  
## <a name="see-also"></a>Weitere Informationen  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>   
 [Mitwirken am Automatisierungs Modell](../../extensibility/internals/contributing-to-the-automation-model.md)   
 [Informationen zu Buildkonfigurationen](../../ide/understanding-build-configurations.md)
