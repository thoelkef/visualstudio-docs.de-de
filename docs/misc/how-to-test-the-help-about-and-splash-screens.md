---
title: "Gewusst wie: Testen von „Hilfe zu“ und Begr&#252;&#223;ungsbildschirmen | Microsoft Docs"
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
  - "Info-Dialogfeld"
  - "VSPackages, Begrüßungsbildschirme"
  - "VSPackages, Branding"
ms.assetid: 2b959fa4-56d3-44f4-8c2d-9ea2e6fb269d
caps.latest.revision: 10
caps.handback.revision: 10
manager: "douge"
---
# Gewusst wie: Testen von „Hilfe zu“ und Begr&#252;&#223;ungsbildschirmen
Nachdem Sie **Hilfe zu** und die Unterstützung der Begrüßungsbildschirm implementieren, können Sie die Implementierung in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]testen.  
  
### So testen Sie die Hilfe zu Dialogfeldern  
  
1.  Von der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Eingabeaufforderung mit dem devenv.exe ausgeführt **\/setup** Schalter.  Um die experimentelle Umgebung ausgeführt werden sollen, geben Sie Folgendes ein:  
  
     **devenv \/rootsuffix Exp \/setup**  
  
     **Hinweis** müssen Sie diesen Schritt wiederholen, wenn Sie die **Hilfe zu** Bildschirm nur Informationen zu ändern.  
  
2.  Ausführen von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] im selben Registrierungsstamm wie weiter oben erwähnt wurde, jedoch ohne den **\/setup** Schalter:  
  
     **devenv \/rootsuffix Exp**  
  
3.  Zeigen Sie im Menü **Hilfe** Informationen.  
  
     Der VSPackage\-Name wird in der **Installierte Produkte** Liste.  
  
4.  Wählen Sie ein VSPackage aus der Liste aus.  
  
     Die VSPackage\-Produktinformation wird im **Produktdetails** Textfeld.  
  
### So testen Sie den Begrüßungsbildschirm  
  
1.  Ausführen von devenv.exe mit dem **\/setup** Schalter.  Um in die experimentelle Umgebung ausgeführt werden, Typ:  
  
     **devenv \/rootsuffix Exp \/setup**  
  
     **Hinweis** müssen Sie diesen Schritt wiederholen, wenn Sie nur den Begrüßungsbildschirm Informationen ändern.  
  
2.  Ausführen von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] im selben Registrierungsstamm wie weiter oben erwähnt wurde, jedoch mit dem **\/splash** Schalter **\/setup** anstelle des Schalters.  
  
     **devenv \/rootsuffix Exp \/splash**  
  
     Die VSPackage\-Produktinformation und das Logo werden auf dem Begrüßungsbildschirm.  
  
## Siehe auch  
 [Branding von VSPackages](../misc/vspackage-branding.md)