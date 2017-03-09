---
title: "Gewusst wie: Branding eines VSPackage (C++) | Microsoft Docs"
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
  - "Info (Dialogfeld)"
  - "VSPackages, Begrüßungsbildschirme"
  - "VSPackages, Branding"
ms.assetid: a1b9213f-8702-4716-8623-cd3705d531fa
caps.latest.revision: 10
caps.handback.revision: 10
manager: "douge"
---
# Gewusst wie: Branding eines VSPackage (C++)
Um im Dialogfeld **Hilfe zu** und im Begrüßungsbildschirm angezeigt wird, muss die VSPackages <xref:Microsoft.VisualStudio.Shell.Interop.IVsInstalledProduct>\-Schnittstelle implementieren.  Auf diese Weise werden die folgenden Informationen an [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]bereit:  
  
-   Name  
  
-   ID, wie Serie oder Versionsnummer  
  
-   Information  
  
-   Symbol für das Logo  
  
 Die `IVsInstalledProductImpl`\-Klasse weist Vorlagenparameter für diese Informationen.  Jeder Vorlagenparameter ist eine ID.  Die ersten drei sind IDs von Zeichenfolgenressourcen und das vierte ist die Ressourcen\-ID des Symbols.  
  
## Beispiel  
 Die folgende Klassendeklaration für die VSPackage\-Klasse ist von [VSSDK\-Beispiele](../misc/vssdk-samples.md).  
  
```  
class ATL_NO_VTABLE BasicPackage :   
  ...  
  public IVsInstalledProductImpl<  
    IDS_BASICPACKAGE_PRODUCT_NAME,  
    IDS_BASICPACKAGE_PRODUCT_IDENTIFIER,   
    IDS_BASICPACKAGE_PRODUCT_DETAILS,   
    IDI_BASICPACKAGE_LOGO>  
```  
  
 Um ein VSPackage zu testen, finden Sie unter [Gewusst wie: Testen von „Hilfe zu“ und Begrüßungsbildschirmen](../misc/how-to-test-the-help-about-and-splash-screens.md).  
  
## Siehe auch  
 [Branding von VSPackages](../misc/vspackage-branding.md)