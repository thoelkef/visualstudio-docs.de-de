---
title: "Visual Studio SDK und verwalteter Code | Microsoft Docs"
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
  - "VSIP, Informationen zu verwaltetem Code"
ms.assetid: 16b3d88e-b5d8-49a5-a5d7-07cbb0b7e4fc
caps.latest.revision: 20
caps.handback.revision: 20
manager: "douge"
---
# Visual Studio SDK und verwalteter Code
*Verwalteter Code* ist Code, der in einer beliebigen Sprache geschrieben wurde, die die Common Language Runtime \(CLR\) wie [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]verwendet oder in [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)].  Unabhängig von der Sprache, dass er geschrieben wird, wird der gesamte verwaltete Code in Microsoft Intermediate Language \(MSIL\) anstelle von systemeigenen Code kompiliert.  
  
## Umgebungs\-Unterstützung für verwaltete VSPackages  
 Um die Erstellung von VSPackages oder Projekt mit einer verwalteten Sprache wie [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]zu unterstützen, stellt [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] Folgendes:  
  
-   Die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Interop\-Assemblys, die VSPackages ermöglichen, die in verwaltetem Code geschrieben wird, um mit der nicht verwalteten \(COM\) [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] integrierten Entwicklungsumgebung \(IDE\) zusammenzuwirken.  Weitere Informationen finden Sie unter [Mithilfe von Interop\-Assemblys von Visual Studio](../extensibility/internals/using-visual-studio-interop-assemblies.md).  
  
-   Ein Satz von Klassen von verwaltetem Paketframeworks \(MPF\), der eine Abstraktion einer höheren Ebene zum Arbeiten mit dem [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE bietet.  Diese Klassen kapseln einige der am häufigsten verwendeten Schnittstellen und der Typen in der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Interop\-Assemblys.  erheblich reduzieren Sie den Arbeitsaufwand, die Sie ausführen müssen, um die Grundfunktionen eines VSPackage oder Projekt bereitzustellen.  Weitere Informationen finden Sie unter [Managed Package Framework\-Klassen](../misc/managed-package-framework-classes.md).  
  
-   Ein Satz von grundlegenden VSPackage\-Beispiele in verwaltetem Code geschrieben.  Die verwaltete auf einem Build. B. B. von einem einfachen, funktionales VSPackage, einen grundlegenden Editor, ein Toolfenster, einen Objekt extender und andere Komponenten vollständig zu veranschaulichen.  Weitere Informationen finden Sie unter [VSSDK\-Beispiele](../misc/vssdk-samples.md).  
  
## Siehe auch  
 [Verwaltete VSPackages](../misc/managed-vspackages.md)   
 [Mithilfe von Interop\-Assemblys von Visual Studio](../extensibility/internals/using-visual-studio-interop-assemblies.md)   
 [Managed Package Framework\-Klassen](../misc/managed-package-framework-classes.md)