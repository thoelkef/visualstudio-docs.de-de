---
title: 'Vorgehensweise: Identifizieren Sie Symbole in einer Bibliothek | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Call Browser tool, identifying symbols in the library
- Call Browser tool
ms.assetid: 8fb0de61-71e7-42d1-8b41-2ad915474384
caps.latest.revision: "21"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6e7f810ff5ad1654081cd061edbc4360eb988402
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-identify-symbols-in-a-library"></a>Vorgehensweise: Identifizieren Sie Symbole in einer Bibliothek
Tools zum Durchsuchen des Symbols anzeigen hierarchische Ansichten der Symbole Die Symbole darstellen, Namespaces, Objekte, Klassen, Klassenmembern und anderen Sprachelemente.  
  
 Jedes Symbol in der Hierarchie kann festgestellt werden, indem die Navigationsinformationen, die von der Symbolbibliothek zu übergeben der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Objektmanager über die folgenden Schnittstellen:  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfoNode>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumNavInfoNodes>.  
  
 Der Speicherort des Symbols in der Hierarchie unterscheidet sich ein Symbol. Tools zum Durchsuchen des Symbols auf ein bestimmtes Symbol navigieren können. Die eindeutige, vollqualifizierte Pfad auf das Symbol bestimmt den Speicherort an. Jedes Element im Pfad ist ein Knoten. Der Pfad beginnt mit dem Knoten der obersten Ebene und endet mit bestimmten Symbols. Beispielsweise ist die M1-Methode ist ein Element der C1-Klasse und C1 befindet sich im N1-Namespace der vollständige Pfad der Methode M1 N1. C1. M1. Dieser Pfad enthält drei Knoten: N1, C1 und M1.  
  
 Ermöglicht die Navigation der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Objekt-Manager suchen, wählen Sie aus, und behalten Sie die Symbole in der Hierarchie ausgewählt. Es ermöglicht das Navigieren zwischen den beiden browsing-Tools zu einem anderen. Bei der Verwendung **Objektkatalog** , suchen Symbole in eine [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] -Projekt können Sie mit der rechten Maustaste, klicken Sie auf eine Methode und Starten der **Aufrufbrowser** Tool, um die Methode in einem Aufrufdiagramm anzuzeigen.  
  
 Zwei Formen werden Symbolspeicherort beschrieben. Die kanonische Form basiert auf den vollqualifizierten Pfad des Symbols. Es stellt eine eindeutige Position des Symbols in der Hierarchie dar. Er ist unabhängig von der Symbolsuche Tool. Zum Abrufen der Informationen zur kanonischen Form der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] -Objekt Manager ruft <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumCanonicalNodes%2A> Methode. Die Präsentationsformat beschreibt den Speicherort des Symbols in ein bestimmtes Symbol durchsuchen-Tool. Die Position des Symbols ist relativ zur Position des anderen Symbolen in der Hierarchicy. Ein bestimmtes Symbol möglicherweise mehrere Presentation-Pfade, aber nur eine kanonischen Pfad. Wenn C1-Klasse wird von der Klasse C2 geerbt und beide Klassen befinden sich im N1-Namespace, z. B. die **Objektkatalog** zeigt die folgenden hierarchische Struktur:  
  
```  
N1  
    C1  
        Bases and Interfaces  
            C2  
    C2  
        Bases and Interfaces  
. . . . . . . . . . .  
  
```  
  
 Der kanonische Pfad der C2-Klasse, in diesem Beispiel ist N1 + C2. Der Pfad der Präsentation von C2 enthält C1 und "Basen und Schnittstellen" Knoten: N1 + C1 + C2 "Basen und Schnittstellen".  
  
 Die Präsentation Formularinformationen der Objekt-Manager-Aufrufe abrufen <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumPresentationNodes%2A> Methode.  
  
## <a name="identifying-a-symbol-in-the-hierarchy"></a>Identifizieren ein Symbol in der Hierarchie  
  
#### <a name="to-obtain-canonical-and-presentation-forms-information"></a>Kanonische abrufen und Präsentation forms Informationen  
  
1.  Implementieren Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumCanonicalNodes%2A>-Methode.  
  
     Der Objekt-Manager ruft diese Methode zum Abrufen der Liste der Knoten, die in den kanonischen Pfad des Symbols enthalten sind.  
  
    ```vb  
    Public Function EnumCanonicalNodes(ByRef ppEnum As Microsoft.VisualStudio.Shell.Interop.IVsEnumNavInfoNodes) As Integer  
        Dim EnumNavInfoNodes As CallBrowserEnumNavInfoNodes = _New CallBrowserEnumNavInfoNodes(m_strMethod)  
        ppEnum = CType(EnumNavInfoNodes, IVsEnumNavInfoNodes)  
        Return 0  
    End Function  
    ```  
  
    ```csharp  
    public int EnumCanonicalNodes(out Microsoft.VisualStudio.Shell.Interop.IVsEnumNavInfoNodes ppEnum)  
    {  
        CallBrowserEnumNavInfoNodes EnumNavInfoNodes =  
            new CallBrowserEnumNavInfoNodes(m_strMethod);  
        ppEnum = (IVsEnumNavInfoNodes)(EnumNavInfoNodes);  
        return 0;  
    }  
  
    ```  
  
2.  Implementieren Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumPresentationNodes%2A>-Methode.  
  
     Der Objekt-Manager ruft diese Methode zum Abrufen der Liste der Knoten in der Präsentation Pfad des Symbols enthalten sind.  
  
## <a name="see-also"></a>Siehe auch  
 [Unterstützung von Tools zum Durchsuchen des Symbols](../../extensibility/internals/supporting-symbol-browsing-tools.md)   
 [Vorgehensweise: Registrieren Sie eine Bibliothek mit dem Objekt-Manager](../../extensibility/internals/how-to-register-a-library-with-the-object-manager.md)   
 [Gewusst wie: Verfügbarmachen der Listen von Symbolen, die von der Bibliothek für den Objekt-Manager bereitgestellt werden](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)