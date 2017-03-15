---
title: "Problembehandlung bei Ausnahmen: System.Runtime.InteropServices.COMException | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "EHCOM"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "COMException-Klasse"
ms.assetid: 14b6de51-e039-4db7-9321-06c9e16e328a
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Problembehandlung bei Ausnahmen: System.Runtime.InteropServices.COMException
Eine <xref:System.Runtime.InteropServices.COMException>\-Ausnahme wird ausgelöst, wenn ein nicht erkanntes HRESULT von einem COM\-Methodenaufruf zurückgegeben wird.  
  
## Tipps  
 **Überprüfen Sie die ErrorCode\-Eigenschaft der Ausnahme, um das vom COM\-Objekt zurückgegebene HRESULT zu bestimmen**  
 Wenn die Laufzeit auf ein unbekanntes HRESULT trifft, wird eine <xref:System.Runtime.InteropServices.COMException>\-Ausnahme ausgelöst. Diese enthält eine öffentliche `ErrorCode`\-Eigenschaft, die das vom Aufruf zurückgegebene HRESULT enthält. Wenn der Laufzeit eine Fehlermeldung vorliegt, wird die Meldung an den Aufrufer zurückgegeben. Wenn der Entwickler der COM\-Komponente jedoch keine Fehlermeldung geschrieben hat, gibt die Laufzeit statt einer Meldungszeichenfolge das achtstellige HRESULT zurück. Mit dem HRESULT kann der Aufrufer die Ursache der Ausnahme bestimmen. Weitere Informationen finden Sie unter [How to: Map HRESULTs and Exceptions](../Topic/How%20to:%20Map%20HRESULTs%20and%20Exceptions.md).  
  
 **Deaktivieren Sie den Hostingprozess.**  
 COM wird verwendet, um zwischen [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] und dem Hostprozess zu kommunizieren. Da COM vor der Codeausführung verwendet wird, bewirkt ein Aufruf von `CoInitializeSecurity`, dass diese Ausnahme ausgelöst wird.  
  
### Hinweise  
 Die Common Language Runtime \(CLR\) wandelt bekannte HRESULTS in .NET\-Ausnahmen um. Auf diese Weise können COM\-Objekte aussagekräftigere Fehlermeldungen an verwaltete Clients zurückgeben. Das Zuordnen von HRESULTS zu Ausnahmen funktioniert auch in die andere Richtung, indem bestimmte HRESULTS an nicht verwaltete Clients zurückgegeben werden.  
  
 Beim Übergeben spät gebundener Parameter an Microsoft Office\-COM\-Objektmethoden wird möglicherweise eine <xref:System.Runtime.InteropServices.COMException> ausgelöst. Das spät bindende Objekt geht davon aus, dass solche Methodenaufrufe einen `ByRef`\-Parameter einschließen und dass die übergebene Eigenschaft über einen `Set`\-Accessor verfügt. Wenn das für die Eigenschaft nicht zutrifft, generiert [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] eine <xref:System.MissingMethodException>\-Ausnahme \(HRESULT CORE\_E\_MISSINGMETHOD\). Um dieses Verhalten zu vermeiden, müssen Sie früh gebundene Objekte verwenden oder eine Variable statt einer Objekteigenschaft übergeben.  
  
## Siehe auch  
 <xref:System.Runtime.InteropServices.COMException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [Behandeln von COM\-Interop\-Ausnahmen](../Topic/Handling%20COM%20Interop%20Exceptions.md)