---
title: Abrufen von Feldbeschreibungen im Eigenschaftenfenster | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- Properties window, field descriptions
ms.assetid: 7d92bb6a-b9b9-4cd8-99e9-b5ee129b52a3
caps.latest.revision: 9
manager: jillfra
ms.openlocfilehash: 1d2b152fd7ed517a238f9893320bd0c36035627c
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "65703980"
---
# <a name="getting-field-descriptions-from-the-properties-window"></a>Abrufen von Feldbeschreibungen im Eigenschaftenfenster
Am unteren Rand des Fensters **Eigenschaften** werden in einem Beschreibungsbereich Informationen angezeigt, die zu dem ausgewählten Eigenschaftenfeld gehören. Diese Funktion ist standardmäßig aktiviert. Wenn Sie das Beschreibungsfeld ausblenden möchten, klicken Sie mit der rechten Maustaste in das Fenster **Eigenschaften** , und klicken Sie auf **Beschreibung**. Dies bewirkt auch, dass das Häkchen neben dem Titel **Beschreibung** im Menüfenster entfernt wird. Sie können das Feld wieder anzeigen, indem die gleichen Schritte ausführen, um **Beschreibung** erneut zu aktivieren.  
  
 Die Informationen im Beschreibungsfeld stammen aus <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo>. Jede Methode, Schnittstelle, Co-Klasse usw. kann ein nicht lokalisiertes `helpstring` Attribut in der Typbibliothek haben. Die **Eigenschaften** Fenster Ruft die Zeichenfolge aus <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo.GetDocumentation%2A>.  
  
### <a name="to-specify-localized-help-strings"></a>So geben Sie lokalisierte Hilfetexte (Hilfezeichenfolgen) an  
  
1. Fügen Sie das `helpstringdll` -Attribut zur library-Anweisung in der Typbibliothek (`typelib`) hinzu.  
  
   > [!NOTE]
   > Dieser Schritt ist optional, wenn sich die Typbibliothek in einer Objektbibliotheksdatei (OLB-Datei) befindet.  
  
2. Geben Sie `helpstringcontext` -Attribute für die Zeichenfolgen an. Sie können auch `helpstring` -Attribute angeben.  
  
    Diese Attribute unterscheiden sich von den Attributen `helpfile` und `helpcontext` , die in den jeweiligen Hilfethemen in CHM-Datei enthalten sind.  
  
   Zum Abrufen der Beschreibungsinformationen für den markierten Eigenschaftennamen angezeigt werden soll die **Eigenschaften** Fenster Aufrufe <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2.GetDocumentation2%2A> für die Eigenschaft, die ausgewählt ist, wobei Sie das gewünschte `lcid` -Attribut für die Ausgabezeichenfolge. Intern findet <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2> die DLL-Datei, die im `helpstringdll`-Attribut angegeben ist, und ruft `DLLGetDocumentation` für diese DLL-Datei mit dem angegebenen Kontext und `lcid`-Attribut auf.  
  
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
  
 Die `DLLGetDocumentation` -Funktion muss ein Export sein, der in der DEF-Datei für die DLL-Datei definiert ist.  
  
 Intern wird eine OLB-Datei erstellt, die tatsächlich eine DLL ist. Diese DLL enthält eine Ressource, die Typbibliotheksdatei (TLB-Datei), und eine exportierte Funktion, `DLLGetDocumentation`.  
  
 Im Fall von OLB-Dateien ist das `helpstringdll` Attribut optional, weil es dieselbe Datei angibt, die selbst die TLB-Datei enthält.  
  
 Wenn Sie möchten, dass Zeichenfolgen abgerufen und im Bereich **Beschreibung** angezeigt werden, ist es daher mindestens erforderlich, dass Sie das `helpstring` -Attribut in der Typbibliothek angeben. Sollen diese Zeichenfolgen lokalisiert sein, müssen Sie das (optionale) `helpstringdll` -Attribut und das (erforderliche) `helpstringcontext` -Attribut angeben sowie `DLLGetDocumentation`implementieren.  
  
 Es gibt keine weiteren Schnittstellen, die implementiert werden müssen, wenn lokalisierte Informationen über das `helpstringcontext` -Attribut und `DLLGetDocumentation`abgerufen werden.  
  
 Eine weitere Möglichkeit zum Abrufen des lokalisierten Namens und der lokalisierten Beschreibung einer Eigenschaft besteht darin, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.GetLocalizedPropertyInfo%2A> zu implementieren. Weitere Informationen über die Implementierung dieser Methode finden Sie unter [Properties Window Fields and Interfaces](../extensibility/internals/properties-window-fields-and-interfaces.md).  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>   
 [Properties Window Fields and Interfaces](../extensibility/internals/properties-window-fields-and-interfaces.md)   
 [Erweitern von Eigenschaften](../extensibility/internals/extending-properties.md)   
 [helpstringdll](https://msdn.microsoft.com/library/121271fa-f061-492b-b87f-bbfcf4b02e7b)   
 [helpstring](https://msdn.microsoft.com/library/0401e905-a63e-4fad-98d0-d1efea111966)   
 [helpstringcontext](https://msdn.microsoft.com/library/d4cd135e-d91c-4aa3-9353-8aeb096f52cf)   
 [helpcontext](https://msdn.microsoft.com/library/6fbb022d-a4b7-4989-a02f-7f18a9b0ad96)   
 [helpfile](https://msdn.microsoft.com/library/d75161c1-1363-4019-ae09-e7e3b8a3971e)   
 [lcid](https://msdn.microsoft.com/library/7f248c69-ee1c-42c3-9411-39cf27c9f43d)