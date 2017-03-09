---
title: "Branding (&#220;bersicht) | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
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
ms.assetid: a47b3645-574c-41c7-8a97-d071cd6b1e82
caps.latest.revision: 11
caps.handback.revision: 11
manager: "douge"
---
# Branding (&#220;bersicht)
So Produktinformationen im Begrüßungsbildschirm oder im **Hilfe zu** Dialogfeld anzeigen, muss ein VSPackage folgende Möglichkeiten:  
  
-   Provide ausführliche Produktinformationen unter dem InstalledProducts\-Registrierungsschlüssel.  
  
     \- oder \-  
  
-   Sie können <xref:Microsoft.VisualStudio.Shell.Interop.IVsInstalledProduct> implementieren.  
  
 Das verwaltete Paketframework \(MPF\) stellt das <xref:Microsoft.VisualStudio.Shell.InstalledProductRegistrationAttribute>\-Attribut auf die Registrierung unter dem InstalledProducts\-Registrierungsschlüssel Steuerelements bereit.  Weitere Informationen finden Sie unter [Gewusst wie: Kennzeichnen eines VSPackages \(C\# und Visual Basic\)](../misc/how-to-brand-a-vspackage-csharp-and-visual-basic.md).  
  
 Die Visual Studio\-Bibliothek stellt die `IVsInstalledProductImpl` Vorlagenklasse, um eine Implementierung von <xref:Microsoft.VisualStudio.Shell.Interop.IVsInstalledProduct>zu erstellen.  Weitere Informationen finden Sie unter [Gewusst wie: Branding eines VSPackage \(C\+\+\)](../misc/how-to-brand-a-vspackage-cpp.md).  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsInstalledProduct> zu implementieren ist explizit leistungsfähiger als die Verwendung des Attributs oder der Vorlage.  
  
-   Sie können ein Begrüßungsbildschirm aus dem das Symbol angeben, **Hilfe zu** Symbol unterscheidet.  
  
-   Sie können einen Begrüßungsbildschirm produkt Namen angeben, der vom **Hilfe zu** Produktnamen unterscheidet.  
  
    > [!IMPORTANT]
    >  Wenn Sie <xref:Microsoft.VisualStudio.Shell.InstalledProductRegistrationAttribute> verwenden und auch <xref:Microsoft.VisualStudio.Shell.Interop.IVsInstalledProduct>die Schnittstelle implementieren, hat Vorrang.  
  
    > [!NOTE]
    >  Dieselbe Symbolressource wird für den Begrüßungsbildschirm und das Dialogfeld **Hilfe zu** verwendet.  Die Ressource muss ein VSPackage\-Symbol 16 × 16 Bild für den Begrüßungsbildschirm 32 × 32 und ein Bild für das **Hilfe zu** Dialogfeld schließen.  Wenn Sie nur eine Bildgröße bereitstellen, wird sie nach Bedarf angepasst, aber die visuelle suboptimal Ergebnisse sind.  
  
 Eine Liste der verwandten Aufgaben finden Sie unter [VSPackages](../extensibility/internals/vspackages.md).  
  
## Siehe auch  
 [VSPackages](../extensibility/internals/vspackages.md)   
 [Visual Studio\-Bibliothek, Übersicht](../misc/visual-studio-library-overview.md)