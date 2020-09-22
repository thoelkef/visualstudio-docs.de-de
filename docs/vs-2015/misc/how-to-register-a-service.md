---
title: 'Vorgehensweise: Registrieren eines Dienstanbieter | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- services, registering
ms.assetid: d086be78-ec3c-43cc-b799-5180a71e19f1
caps.latest.revision: 16
manager: jillfra
ms.openlocfilehash: f41578f2522487f746a469933a2269a621390f3c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90840880"
---
# <a name="how-to-register-a-service"></a>Gewusst wie: Registrieren von Diensten
Managed Package Framework (MPF) stellt Attribute bereit, um die Registrierung der verwalteten Dienste zu steuern. Das RegPkg-Dienstprogramm verwendet diese Attribute zum Registrieren eines Diensts mit [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
## <a name="example"></a>Beispiel  
 Der folgende Code ist aus [VSSDK-Beispielen](../misc/vssdk-samples.md).  
  
 [!code-csharp[VSSDKRegisterService#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkregisterservice/cs/vssdkregisterservicepackage.cs#1)]
 [!code-vb[VSSDKRegisterService#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkregisterservice/vb/vssdkregisterservicepackage.vb#1)]  
  
 <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> registriert den Dienst SMyGlobalService mit [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Weitere Informationen zu <xref:Microsoft.VisualStudio.Shell.DefaultRegistryRootAttribute> und <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> finden Sie unter [registrieren und Aufheben der Registrierung von VSPackages](../extensibility/registering-and-unregistering-vspackages.md).  
  
 Verwenden Sie <xref:Microsoft.VisualStudio.Shell.ProvideServiceOverrideAttribute> statt <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute>, um einen Dienst zu registrieren, der einen anderen Dienst gleichen Namens ersetzt.  
  
## <a name="robust-programming"></a>Stabile Programmierung  
 Um das erneute Kompilieren eines Dienstanbieters ohne Änderung des Dienstclients (oder umgekehrt) zu vereinfachen, können Sie den Dienst und die zugehörigen Schnittstellen in einem separaten Assembly-Modul definieren. Der folgende Code stammt aus der Datei "IMyGlobalService.cs" im Reference.Services (C#)-Beispiel.  
  
 [!code-csharp[VSSDKRegisterService#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkregisterservice/cs/vssdkregisterservicepackage.cs#2)]
 [!code-vb[VSSDKRegisterService#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkregisterservice/vb/vssdkregisterservicepackage.vb#2)]  
  
 <xref:System.Runtime.InteropServices.ComVisibleAttribute> ist erforderlich, um die Schnittstelle aus nicht verwaltetem Code abzurufen.  
  
> [!NOTE]
> Sie können zwar den gleichen Typ oder die GUID für den Dienst und die Schnittstelle verwenden, es ist jedoch empfehlenswert, die beiden zu trennen, da der Dienst unterschiedliche Schnittstellen verfügbar machen kann.  
  
## <a name="see-also"></a>Weitere Informationen  
 [VSPackages werden registriert](../extensibility/internals/registering-vspackages.md)   
 [Dienstgrundlagen](../extensibility/internals/service-essentials.md)