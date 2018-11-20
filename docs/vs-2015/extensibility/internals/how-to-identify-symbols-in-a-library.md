---
title: 'Vorgehensweise: Identifizieren von Symbolen in einer Bibliothek | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Call Browser tool, identifying symbols in the library
- Call Browser tool
ms.assetid: 8fb0de61-71e7-42d1-8b41-2ad915474384
caps.latest.revision: 22
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 34b5480aebbe59ef9b023bf4350b2bdd35725c47
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51786703"
---
# <a name="how-to-identify-symbols-in-a-library"></a>Vorgehensweise: Identifizieren von Symbolen in einer Bibliothek
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Tools zum Durchsuchen von Symbolen angezeigt hierarchische Ansichten von Symbolen. Die Symbole darstellen, Namespaces, Objekte, Klassen, Klassenmembern und anderen Sprachelemente.  
  
 Jedes Symbol in der Hierarchie identifiziert werden kann, durch die Navigationsinformationen durch die Symbolbibliothek zum Übergeben der [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] -Objekt-Manager über die folgenden Schnittstellen:  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfoNode>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumNavInfoNodes>.  
  
 Der Speicherort des Symbols in der Hierarchie unterscheidet es sich um ein Symbol. Sie können die Tools zum Durchsuchen von Symbol, um auf ein bestimmtes Symbol zu navigieren. Die eindeutige, vollqualifizierte Pfad zur symbolspeicherfreigabe bestimmt den Speicherort an. Jedes Element im Pfad ist ein Knoten. Der Pfad mit den obersten Knoten beginnt und endet mit dem spezifischen Symbol. Wenn die Methode M1 ein Element der C1-Klasse ist, und C1 befindet sich im N1-Namespace, lautet der vollständige Pfad der Methode M1 N1. C1. M1. Dieser Pfad enthält drei Knoten: N1, C1 und M1.  
  
 Mit diesen Navigationsinformationen können die [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] -Objekt-Manager suchen, wählen Sie aus, und behalten Sie die Symbole in der Hierarchie ausgewählt. Es ermöglicht das Navigieren von einem Browsingtool in einen anderen. Bei der Verwendung von **Objektkatalog** zum Durchsuchen von Symbolen in einem [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] -Projekt, Sie klicken Sie mit der rechten Maustaste auf eine Methode, und Starten der **Aufrufbrowser** Tool, um die Methode in einem Aufrufdiagramm anzeigen.  
  
 Zwei Arten beschreiben den Symbolspeicherort. Die kanonische Form basiert auf den vollqualifizierten Pfad des Symbols. Es stellt eine eindeutige Position des Symbols in der Hierarchie dar. Er ist unabhängig von dem Tool zum Durchsuchen von Symbolen. Die kanonische Formularinformationen abgerufen, die [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Objekt-Manager-Aufrufe <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumCanonicalNodes%2A> Methode. Die Präsentationsformat beschreibt den Speicherort des Symbols in einer bestimmten symbolsuchtool. Die Position des Symbols ist relativ zur Position der andere Symbole in der Hierarchicy. Ein bestimmtes Symbol möglicherweise mehrere Presentation-Pfade, aber nur einen kanonischen Pfad. Wenn C1-Klasse aus der C2-Klasse geerbt wird, und beide Klassen befinden sich im N1-Namespace, z. B. die **Objektkatalog** der folgende hierarchische Struktur angezeigt:  
  
```  
N1  
    C1  
        Bases and Interfaces  
            C2  
    C2  
        Bases and Interfaces  
. . . . . . . . . . .  
  
```  
  
 Die kanonische Pfad des C2-Klasse, in diesem Beispiel ist N1 + C2. Präsentationspfad des C2 enthält der Knoten "C1" und "Basen und Schnittstellen": N1 + C1 + C2 "Basen und Schnittstellen".  
  
 Zum Abrufen von Informationen der Präsentation Form, der die Objekt-Manager ruft <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumPresentationNodes%2A> Methode.  
  
## <a name="identifying-a-symbol-in-the-hierarchy"></a>Identifiziert ein Symbol in der Hierarchie  
  
#### <a name="to-obtain-canonical-and-presentation-forms-information"></a>Kanonische abrufen und Presentation forms-Informationen  
  
1.  Implementieren Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumCanonicalNodes%2A>-Methode.  
  
     Der Objekt-Manager ruft diese Methode zum Abrufen der Liste von Knoten im kanonischen Pfad des Symbols enthalten sind.  
  
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
  
     Der Objekt-Manager ruft diese Methode zum Abrufen der Liste von Knoten im Präsentationspfad des Symbols enthalten sind.  
  
## <a name="see-also"></a>Siehe auch  
 [Unterstützung von Tools zum Durchsuchen von Symbolen](../../extensibility/internals/supporting-symbol-browsing-tools.md)   
 [Vorgehensweise: Registrieren einer Bibliothek mit der Objekt-Manager](../../extensibility/internals/how-to-register-a-library-with-the-object-manager.md)   
 [Gewusst wie: Verfügbarmachen der Listen von Symbolen, die von der Bibliothek für den Objekt-Manager bereitgestellt werden](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)

