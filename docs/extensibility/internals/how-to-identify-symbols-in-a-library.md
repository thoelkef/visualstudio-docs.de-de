---
title: 'Gewusst wie: Identifizieren von Symbolen in einer Bibliothek | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Call Browser tool, identifying symbols in the library
- Call Browser tool
ms.assetid: 8fb0de61-71e7-42d1-8b41-2ad915474384
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1fe920fabd05a875b336467fbba16e4229fa9613
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708004"
---
# <a name="how-to-identify-symbols-in-a-library"></a>Gewusst wie: Identifizieren von Symbolen in einer Bibliothek
Symbol-Browsing-Tools zeigen hierarchische Ansichten von Symbolen an. Die Symbole stellen Namespaces, Objekte, Klassen, Klassenmember und andere Sprachelemente dar.

 Jedes Symbol in der Hierarchie kann durch die Navigationsinformationen [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] identifiziert werden, die von der Symbolbibliothek über die folgenden Schnittstellen an den Objekt-Manager übergeben werden:

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfoNode>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumNavInfoNodes>.

 Die Position des Symbols in der Hierarchie unterscheidet ein Symbol. Es ermöglicht Symbol-Browsing-Tools zu einem bestimmten Symbol zu navigieren. Der eindeutige, vollqualifizierte Pfad zum Symbol bestimmt die Position. Jedes Element im Pfad ist ein Knoten. Der Pfad beginnt mit dem Knoten der obersten Ebene und endet mit dem spezifischen Symbol. Wenn die M1-Methode beispielsweise ein Member der C1-Klasse ist und C1 sich im N1-Namespace befindet, lautet der vollständige Pfad der M1-Methode N1. C1. M1. Dieser Pfad enthält drei Knoten: N1, C1 und M1.

 Die Navigationsinformationen [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ermöglichen es dem Objekt-Manager, die Ausgewählten Symbole in der Hierarchie zu suchen, auszuwählen und zu behalten. Es ermöglicht das Navigieren von einem Browser-Tool zu einem anderen. Wenn Sie **den Objektbrowser** [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] zum Durchsuchen von Symbolen in einem Projekt verwenden, können Sie mit der rechten Maustaste auf eine Methode klicken und das Werkzeug **Browser aufrufen** starten, um die Methode in einem Aufrufdiagramm anzuzeigen.

 Zwei Formulare beschreiben die Symbolposition. Die kanonische Form basiert auf dem vollqualifizierten Pfad des Symbols. Es stellt eine eindeutige Position des Symbols in der Hierarchie dar. Es ist unabhängig vom Symbol-Browsing-Tool. Um die kanonischen Formularinformationen [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] abzuerhalten, ruft der Objekt-Manager die Methode auf. <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumCanonicalNodes%2A> Das Präsentationsformular beschreibt die Position des Symbols in einem bestimmten Symbol-Browsing-Tool. Die Position des Symbols ist relativ zur Position anderer Symbole in der Hierarchie. Ein bestimmtes Symbol kann mehrere Präsentationspfade haben, aber nur einen kanonischen Pfad. Wenn z. B. die C1-Klasse von der C2-Klasse geerbt wird und sich beide Klassen im N1-Namespace befinden, zeigt der **Objektbrowser** die folgende hierarchische Struktur an:

```
N1
    C1
        Bases and Interfaces
            C2
    C2
        Bases and Interfaces
. . . . . . . . . . .

```

 Der kanonische Pfad der C2-Klasse ist in diesem Beispiel N1 + C2. Der Präsentationspfad von C2 umfasst C1- und "Bases and Interfaces"-Knoten: N1 + C1 + "Basen und Schnittstellen" + C2.

 Um die Präsentationsformularinformationen abzuerhalten, ruft der Objekt-Manager die Methode auf. <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumPresentationNodes%2A>

## <a name="to-obtain-canonical-and-presentation-forms-information"></a>Informationen zu kanonischen und Präsentationsformularen

1. Implementieren Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumCanonicalNodes%2A>-Methode.

     Der Objekt-Manager ruft diese Methode auf, um die Liste der Knoten abzufragen, die im kanonischen Pfad des Symbols enthalten sind.

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

2. Implementieren Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumPresentationNodes%2A>-Methode.

     Der Objekt-Manager ruft diese Methode auf, um die Liste der Knoten abzuholen, die im Präsentationspfad des Symbols enthalten sind.

## <a name="see-also"></a>Weitere Informationen
- [Unterstützung von Symbol-Browsing-Tools](../../extensibility/internals/supporting-symbol-browsing-tools.md)
- [Gewusst wie: Registrieren einer Bibliothek beim Objektmanager](../../extensibility/internals/how-to-register-a-library-with-the-object-manager.md)
- [Gewusst wie: Listen mit Symbolen, die von der Bibliothek bereitgestellt werden, für den Objektmanager verfügbar machen](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)
