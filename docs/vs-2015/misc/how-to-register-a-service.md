---
title: 'Vorgehensweise: Registrieren von Diensten | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- services, registering
ms.assetid: d086be78-ec3c-43cc-b799-5180a71e19f1
caps.latest.revision: 16
manager: jillfra
ms.openlocfilehash: 0ec69fa123775cb477195d4022fb439fb990f415
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "59001647"
---
# <a name="how-to-register-a-service"></a>Vorgehensweise: Registrieren von Diensten
Managed Package Framework (MPF) stellt Attribute bereit, um die Registrierung der verwalteten Dienste zu steuern. Das RegPkg-Dienstprogramm verwendet diese Attribute zum Registrieren eines Diensts mit [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
## <a name="example"></a>Beispiel  
 Der folgende Code stammt aus [VSSDK-Beispiele](../misc/vssdk-samples.md).  
  
 [!code-csharp[VSSDKRegisterService#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkregisterservice/cs/vssdkregisterservicepackage.cs#1)]
 [!code-vb[VSSDKRegisterService#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkregisterservice/vb/vssdkregisterservicepackage.vb#1)]  
  
 <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> registriert den Dienst SMyGlobalService mit [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Weitere Informationen zu <xref:Microsoft.VisualStudio.Shell.DefaultRegistryRootAttribute> und <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>, finden Sie unter [registrieren und Aufheben der Registrierung des VSPackages](../extensibility/registering-and-unregistering-vspackages.md).  
  
 Verwenden Sie <xref:Microsoft.VisualStudio.Shell.ProvideServiceOverrideAttribute> statt <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute>, um einen Dienst zu registrieren, der einen anderen Dienst gleichen Namens ersetzt.  
  
## <a name="robust-programming"></a>Stabile Programmierung  
 Um das erneute Kompilieren eines Dienstanbieters ohne Änderung des Dienstclients (oder umgekehrt) zu vereinfachen, können Sie den Dienst und die zugehörigen Schnittstellen in einem separaten Assembly-Modul definieren. Der folgende Code stammt aus der Datei "IMyGlobalService.cs" im Reference.Services (C#)-Beispiel.  
  
 [!code-csharp[VSSDKRegisterService#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkregisterservice/cs/vssdkregisterservicepackage.cs#2)]
 [!code-vb[VSSDKRegisterService#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkregisterservice/vb/vssdkregisterservicepackage.vb#2)]  
  
 <xref:System.Runtime.InteropServices.ComVisibleAttribute> ist erforderlich, um die Schnittstelle aus nicht verwaltetem Code abzurufen.  
  
> [!NOTE]
>  Sie können zwar den gleichen Typ oder die GUID für den Dienst und die Schnittstelle verwenden, es ist jedoch empfehlenswert, die beiden zu trennen, da der Dienst unterschiedliche Schnittstellen verfügbar machen kann.  
  
## <a name="see-also"></a>Siehe auch  
 [Registrieren von VSPackages](../extensibility/internals/registering-vspackages.md)   
 [Dienstgrundlagen](../extensibility/internals/service-essentials.md)