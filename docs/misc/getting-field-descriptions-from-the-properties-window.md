---
title: "Abrufen von Feldbeschreibungen im Eigenschaftenfenster | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Eigenschaftenfenster, Feldbeschreibungen"
ms.assetid: 7d92bb6a-b9b9-4cd8-99e9-b5ee129b52a3
caps.latest.revision: 9
caps.handback.revision: 9
manager: "douge"
---
# Abrufen von Feldbeschreibungen im Eigenschaftenfenster
Am unteren Rand des Fensters **Eigenschaften** werden in einem Beschreibungsbereich Informationen angezeigt, die zu dem ausgewählten Eigenschaftenfeld gehören. Diese Funktion ist standardmäßig aktiviert. Wenn Sie das Beschreibungsfeld ausblenden möchten, klicken Sie mit der rechten Maustaste in das Fenster **Eigenschaften**, und klicken Sie auf **Beschreibung**. Dies bewirkt auch, dass das Häkchen neben dem Titel **Beschreibung** im Menüfenster entfernt wird. Sie können das Feld wieder anzeigen, indem die gleichen Schritte ausführen, um **Beschreibung** erneut zu aktivieren.  
  
 Die Informationen im Beschreibungsfeld stammen aus <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo>. Jede Methode, Schnittstelle, Co\-Klasse usw. kann ein nicht lokalisiertes`helpstring`Attribut in der Typbibliothek haben. Das Fenster **Eigenschaften** ruft die Zeichenfolge aus <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo.GetDocumentation%2A> ab.  
  
### So geben Sie lokalisierte Hilfetexte \(Hilfezeichenfolgen\) an  
  
1.  Fügen Sie das `helpstringdll`\-Attribut zur library\-Anweisung in der Typbibliothek \(`typelib`\) hinzu.  
  
    > [!NOTE]
    >  Dieser Schritt ist optional, wenn sich die Typbibliothek in einer Objektbibliotheksdatei \(OLB\-Datei\) befindet.  
  
2.  Geben Sie `helpstringcontext`\-Attribute für die Zeichenfolgen an. Sie können auch `helpstring`\-Attribute angeben.  
  
     Diese Attribute unterscheiden sich von den Attributen `helpfile` und `helpcontext`, die in den jeweiligen Hilfethemen in CHM\-Datei enthalten sind.  
  
 Um die Beschreibungsinformationen abzurufen, die für den markierten Eigenschaftennamen angezeigt werden sollen, ruft das Fenster **Eigenschaften** die <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2.GetDocumentation2%2A>\-Methode für die ausgewählte Eigenschaft auf, wobei sie das gewünschte `lcid`\-Attribut für die Ausgabezeichenfolge angibt. Intern findet <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2> die DLL\-Datei, die im `helpstringdll`\-Attribut angegeben ist, und ruft `DLLGetDocumentation` für diese DLL\-Datei mit dem angegebenen Kontext und `lcid`\-Attribut auf.  
  
 Die Signatur und die Implementierung von `DLLGetDocumentation` sind:  
  
```  
STDAPI DLLGetDocumentation  
(  
   ITypeLib * /* ptlib */,  
   ITypeInfo * /* ptinfo */,  
   LCID /* lcid */,  
   DWORD dwCtx,  
   BSTR * pbstrHelpString  
);  
```  
  
 Die `DLLGetDocumentation`\-Funktion muss ein Export sein, der in der DEF\-Datei für die DLL\-Datei definiert ist.  
  
 Intern wird eine OLB\-Datei erstellt, die tatsächlich eine DLL ist. Diese DLL enthält eine Ressource, die Typbibliotheksdatei \(TLB\-Datei\), und eine exportierte Funktion, `DLLGetDocumentation`.  
  
 Im Fall von OLB\-Dateien ist das `helpstringdll`Attribut optional, weil es dieselbe Datei angibt, die selbst die TLB\-Datei enthält.  
  
 Wenn Sie möchten, dass Zeichenfolgen abgerufen und im Bereich **Beschreibung** angezeigt werden, ist es daher mindestens erforderlich, dass Sie das `helpstring`\-Attribut in der Typbibliothek angeben. Sollen diese Zeichenfolgen lokalisiert sein, müssen Sie das \(optionale\) `helpstringdll`\-Attribut und das \(erforderliche\) `helpstringcontext`\-Attribut angeben sowie `DLLGetDocumentation` implementieren.  
  
 Es gibt keine weiteren Schnittstellen, die implementiert werden müssen, wenn lokalisierte Informationen über das `helpstringcontext`\-Attribut und `DLLGetDocumentation` abgerufen werden.  
  
 Eine weitere Möglichkeit zum Abrufen des lokalisierten Namens und der lokalisierten Beschreibung einer Eigenschaft besteht darin, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.GetLocalizedPropertyInfo%2A> zu implementieren. Weitere Informationen über die Implementierung dieser Methode finden Sie unter [Eigenschaften\-Fenster Felder und Schnittstellen](../extensibility/internals/properties-window-fields-and-interfaces.md).  
  
## Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>   
 [Eigenschaften\-Fenster Felder und Schnittstellen](../extensibility/internals/properties-window-fields-and-interfaces.md)   
 [Erweitern von Eigenschaften](../extensibility/internals/extending-properties.md)   
 [helpstringdll](/visual-cpp/windows/helpstringdll)   
 [helpstring](/visual-cpp/windows/helpstring)   
 [helpstringcontext](/visual-cpp/windows/helpstringcontext)   
 [helpcontext](/visual-cpp/windows/helpcontext)   
 [helpfile](/visual-cpp/windows/helpfile)   
 [lcid](/visual-cpp/windows/lcid)