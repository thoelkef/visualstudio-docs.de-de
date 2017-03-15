---
title: "Gewusst wie: Registrieren von Diensten | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Dienste, Registrieren"
ms.assetid: d086be78-ec3c-43cc-b799-5180a71e19f1
caps.latest.revision: 16
caps.handback.revision: 16
manager: "douge"
---
# Gewusst wie: Registrieren von Diensten
Managed Package Framework \(MPF\) stellt Attribute bereit, um die Registrierung der verwalteten Dienste zu steuern. Das RegPkg\-Dienstprogramm verwendet diese Attribute zum Registrieren eines Diensts mit [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## Beispiel  
 Der folgende Code stammt aus [VSSDK\-Beispiele](../misc/vssdk-samples.md).  
  
 [!code-vb[VSSDKRegisterService#1](../misc/codesnippet/VisualBasic/how-to-register-a-service_1.vb)]
 [!code-cs[VSSDKRegisterService#1](../misc/codesnippet/CSharp/how-to-register-a-service_1.cs)]  
  
 <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> registriert den Dienst SMyGlobalService mit [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Weitere Informationen zu <xref:Microsoft.VisualStudio.Shell.DefaultRegistryRootAttribute> und <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> finden Sie unter [Registrieren und Aufheben der Registrierung von VSPackages](../extensibility/registering-and-unregistering-vspackages.md).  
  
 Verwenden Sie <xref:Microsoft.VisualStudio.Shell.ProvideServiceOverrideAttribute> statt <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute>, um einen Dienst zu registrieren, der einen anderen Dienst gleichen Namens ersetzt.  
  
## Robuste Programmierung  
 Um das erneute Kompilieren eines Dienstanbieters ohne Änderung des Dienstclients \(oder umgekehrt\) zu vereinfachen, können Sie den Dienst und die zugehörigen Schnittstellen in einem separaten Assembly\-Modul definieren. Der folgende Code stammt aus der Datei "IMyGlobalService.cs" im Reference.Services \(C\#\)\-Beispiel.  
  
 [!code-vb[VSSDKRegisterService#2](../misc/codesnippet/VisualBasic/how-to-register-a-service_2.vb)]
 [!code-cs[VSSDKRegisterService#2](../misc/codesnippet/CSharp/how-to-register-a-service_2.cs)]  
  
 <xref:System.Runtime.InteropServices.ComVisibleAttribute> ist erforderlich, um die Schnittstelle aus nicht verwaltetem Code abzurufen.  
  
> [!NOTE]
>  Sie können zwar den gleichen Typ oder die GUID für den Dienst und die Schnittstelle verwenden, es ist jedoch empfehlenswert, die beiden zu trennen, da der Dienst unterschiedliche Schnittstellen verfügbar machen kann.  
  
## Siehe auch  
 [Registering VSPackages](http://msdn.microsoft.com/de-de/31e6050f-1457-4849-944a-a3c36b76f3dd)   
 [Service – Grundlagen](../extensibility/internals/service-essentials.md)