---
title: "Gewusst wie: Identifizieren von Objekten in einer Bibliothek | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Rufen Sie Browser-Tool, identifizieren die Symbole in der Bibliothek"
  - "Rufen Sie Browser-tool"
ms.assetid: 8fb0de61-71e7-42d1-8b41-2ad915474384
caps.latest.revision: 21
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 21
---
# Gewusst wie: Identifizieren von Objekten in einer Bibliothek
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

hierarchische Ansichten der Symbol\-Durchsuchen Tool\-Anzeige von Symbolen.  Die Symbole stellen Namespaces, Klassen, Objekten und andere Klassenmember Sprachelemente dar.  
  
 Jedes Symbol in der Hierarchie kann durch die Informationen zur Navigation bezeichnet werden, die von der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] dem Symbol Library Manager Objekt über die folgenden Schnittstellen übergeben werden:  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfoNode>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumNavInfoNodes>.  
  
 Die Position des Symbols in der Hierarchie unterscheidet ein Symbol.  Dies ermöglicht es Tools Symbol Durchsuchen, um zu einem bestimmten Symbols zu navigieren.  Das eindeutige, vollqualifizierter Pfad zu dem Symbol bestimmt die Position.  Jedes Element im Pfad ist ein Knoten.  Der Pfad beginnt mit dem Knoten der obersten Ebene und endet mit dem Symbol.  Wenn beispielsweise die Methode M1 Mitglied der C1\- Klasse befindet und dem Namespace C1 N1 ist, ist der vollständige Pfad der Methode M1 N1. C1. M1.  Dieser Pfad enthält drei Knoten: N1, C1 und M1.  
  
 Die Informationen zur Navigation ermöglichen es dem Objekt [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Manager, nach denen gesucht werden soll, halten auswählen und wählte die Symbole in der Hierarchie aus.  Sie ermöglicht die Navigation von einem anderen Tool zu durchsuchenden.  Wie kann die Verwendung von **Objektkatalog** , um Symbole in einem [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]\-Projekt zum Durchsuchen Sie mit der rechten Maustaste auf eine Methode und das **Aufrufbrowser** Tool starten, um die Methode in einem Aufrufdiagramm anzuzeigen.  
  
 Zwei Arten beschreiben den Speicherort des Symbols.  Die kanonische Form basiert auf den vollqualifizierten Pfad des Symbols.  Sie stellt eine einzigartige Zustand des Symbols in der Hierarchie dar.  Dies ist unabhängig vom Symbol Durchsuchen Tools.  Zum Abrufen der Informationen der kanonische Form, ruft der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Manager Objekt <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumCanonicalNodes%2A>\-Methode veranschaulicht.  Das Präsentations Form beschreibt die Position des Symbols in einem bestimmten Symbols Durchsuchen Tools.  Die Position des Symbols ist relativ zur Position anderer Symbole im hierarchicy.  Ein bestimmtes Symbol verfügt möglicherweise über mehrere Präsentations, jedoch nur für einen kanonischen Pfad.  Wenn z. B. C1\- Klasse von C2\- Klasse geerbt wird, und beide Klassen im Namespace N1 sind, wird die folgende **Objektkatalog** hierarchischen Struktur an:  
  
```  
N1  
    C1  
        Bases and Interfaces  
            C2  
    C2  
        Bases and Interfaces  
. . . . . . . . . . .  
  
```  
  
 Der kanonische Pfad von C2\- Klasse in diesem Beispiel ist C2 \+ N1.  Der Pfad der C2 schließt Präsentations C1\- und „Basis\- und Schnittstellen“ Knoten ein: N1 \+ C1 \+ „.“ \+ C2 Basisklassen und Schnittstellen.  
  
 Zum Abrufen der Form Präsentations Informationen, ruft der Objekt Manager <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumPresentationNodes%2A>\-Methode veranschaulicht.  
  
## Identifizieren eines Symbols in der Hierarchie  
  
#### So rufen Sie Informationen zu Präsentations und kanonische Form  
  
1.  Implementieren Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumCanonicalNodes%2A>\-Methode.  
  
     Der Manager Objekt ruft diese Methode auf, um die Liste der zu erhalten, die sich im Knoten enthaltenen kanonischen Pfad des Symbols enthalten sind.  
  
    ```vb#  
    Public Function EnumCanonicalNodes(ByRef ppEnum As Microsoft.VisualStudio.Shell.Interop.IVsEnumNavInfoNodes) As Integer  
        Dim EnumNavInfoNodes As CallBrowserEnumNavInfoNodes = _New CallBrowserEnumNavInfoNodes(m_strMethod)  
        ppEnum = CType(EnumNavInfoNodes, IVsEnumNavInfoNodes)  
        Return 0  
    End Function  
    ```  
  
    ```c#  
    public int EnumCanonicalNodes(out Microsoft.VisualStudio.Shell.Interop.IVsEnumNavInfoNodes ppEnum)  
    {  
        CallBrowserEnumNavInfoNodes EnumNavInfoNodes =  
            new CallBrowserEnumNavInfoNodes(m_strMethod);  
        ppEnum = (IVsEnumNavInfoNodes)(EnumNavInfoNodes);  
        return 0;  
    }  
  
    ```  
  
2.  Implementieren Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumPresentationNodes%2A>\-Methode.  
  
     Der Manager Objekt ruft diese Methode auf, um die Liste der zu erhalten, die den Knoten im Pfad Präsentations das Symbol enthalten sind.  
  
## Siehe auch  
 [Unterstützung von Tools zum Durchsuchen des Symbols](../../extensibility/internals/supporting-symbol-browsing-tools.md)   
 [Gewusst wie: Registrieren eine Bibliothek mit der Objekt\-Manager](../../extensibility/internals/how-to-register-a-library-with-the-object-manager.md)   
 [Gewusst wie: Listen von Symbolen, die von der Bibliothek bereitgestellt, der Objekt\-Manager verfügbar machen](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)