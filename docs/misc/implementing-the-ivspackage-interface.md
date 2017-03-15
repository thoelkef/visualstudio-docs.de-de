---
title: "Implementieren der IVsPackage-Schnittstelle | Microsoft Docs"
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
  - "IVsPackage-Schnittstelle"
  - "Schnittstellen, IVsPackages implementieren"
ms.assetid: 0c76b2e1-ce63-47fc-93ee-847cad281fc1
caps.latest.revision: 12
caps.handback.revision: 12
manager: "douge"
---
# Implementieren der IVsPackage-Schnittstelle
Alle VSPackages muss die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>\-Schnittstelle implementieren.  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ruft die Methoden von <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> an, die VSPackages zu initialisieren und zugeordneten Eigenschaftenseiten zu schließen und aus anderen Gründen.  Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>\-Schnittstelle ist die Schnittstelle zwischen Gateway [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] und VSPackages.  
  
 Sie können einen verwalteten VSPackages als Unterklasse der <xref:Microsoft.VisualStudio.Shell.Package>\-Klasse schreiben, die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> im Namen implementiert.  Weitere Informationen finden Sie unter [Verwaltete VSPackages](../misc/managed-vspackages.md).  
  
> [!NOTE]
>  Ein Großteil des nicht verwalteten Beispielcodes in Visual Studio\-Integrations [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)]\-Abschnitt wird die Active Template Library \(ATL\).  Sie müssen keine ATL verwenden, um VSPackages zu erstellen. Sie müssen jedoch ATL verstehen, um den Beispielcode zu verstehen.  
  
## Siehe auch  
 [VSPackages](../extensibility/internals/vspackages.md)