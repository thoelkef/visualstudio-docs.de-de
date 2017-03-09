---
title: "Cannot find custom tool &#39;custom tool&#39; on this system | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.cannot_instantiate_generator1"
ms.assetid: 51fe9bec-b8bc-4a4c-94aa-15a1f7cc8b6b
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Cannot find custom tool &#39;custom tool&#39; on this system
Das benutzerdefinierte Tool kann vom Projektsystem nicht erstellt werden.  Das angeforderte benutzerdefinierte Tool wird nicht ausgeführt, weil das Projektsystem es nicht instanziieren kann.  Vergewissern Sie sich, dass das benutzerdefinierte Tool ordnungsgemäß installiert und registriert wurde.  
  
 Dieser Fehler kann auftreten, wenn für eine bestimmte Datei ein ungültiger Name des benutzerdefinierten Tools für die `CustomTool`\-Eigenschaft angegeben wurde.  Es ist auch möglich, dass die Projektdatei \(**.vbproj\/.csproj**\) bearbeitet wurde und der Wert für die `CustomTool`\-Eigenschaft dadurch ungültig geworden ist.  Sie können auch ein Projekt verwenden, das auf einem anderen Computer entwickelt wurde und das benutzerdefinierte Tool enthält, während dieses Tool auf dem Computer nicht installiert ist.  Weitere Informationen zur `CustomTool`\-Eigenschaft finden Sie unter [File Properties](http://msdn.microsoft.com/de-de/013c4aed-08d6-4dce-a124-ca807ca08959).  
  
 Dieser Fehler kann auch auftreten, wenn [CComPtrBase::CoCreateInstance](../Topic/CComPtrBase::CoCreateInstance.md) für das benutzerdefinierte Tool fehlschlägt.  Möglicherweise ist es nicht registriert oder eine erforderliche DLL fehlt.  
  
## Siehe auch  
 [CComPtrBase::CoCreateInstance](../Topic/CComPtrBase::CoCreateInstance.md)