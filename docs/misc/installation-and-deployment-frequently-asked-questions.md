---
title: "Installation und Bereitstellung – h&#228;ufig gestellte Fragen | Microsoft Docs"
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
  - "Bereitstellung [Visual Studio SDK]"
  - "LCID [Visual Studio SDK]"
  - "Installation [Visual Studio SDK]"
ms.assetid: 4ac62bf3-e335-4899-9074-89bcd004dc65
caps.latest.revision: 10
caps.handback.revision: 10
manager: "douge"
---
# Installation und Bereitstellung – h&#228;ufig gestellte Fragen
Dieses Thema bezieht sich auf von der Abfrage [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] community Benutzer über die Installation und Bereitstellung an.  In diesem Thema wird fortgesetzt, mit neuem Inhalt aus der Community, die aktualisiert werden soll.  
  
## Inhalt  
  
-   [Die LCID einer Visual Studio-Installation programmgesteuert bestimmen](#DeterminingtheLCIDofaVisualStudioInstallationProgrammatically)  
  
##  <a name="DeterminingtheLCIDofaVisualStudioInstallationProgrammatically"></a> Die LCID einer Visual Studio\-Installation programmgesteuert bestimmen  
 **Q:** Gibt es eine Methode, die LCID einer Installation [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] programmgesteuert bestimmen?  
  
 **A:**  <xref:Microsoft.VisualStudio.Shell.Interop.IUIHostLocale2.GetUILocale%2A> oder <xref:Microsoft.VisualStudio.Shell.Interop.IUIHostLocale.GetUILocale%2A>geben die LCID [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] der derzeit verwendeten zurück.  
  
## Siehe auch  
 [Freigeben eines Produkts](../misc/releasing-a-visual-studio-integration-product.md)