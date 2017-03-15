---
title: "COM Interop unregistration failed | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.cannot_unregister_com2"
ms.assetid: 1172b560-c4b0-4aff-9f74-cf9b29ff76d9
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# COM Interop unregistration failed
Beim Aufheben der Registrierung einer alten Kopie der Assembly ist ein Problem aufgetreten.  
  
 Wenn die Eigenschaft **Für COM\-Interop registrieren** festgelegt wurde, versucht das Projektsystem zuerst, die Registrierung einer alten Kopie des COM\-Objekts aufzuheben, bevor die gerade erstellte Kopie registriert wird.  Dieser Schritt ist erforderlich, um die Registrierung auf dem aktuellen Stand zu halten.  
  
 Informationen zum Zugreifen auf die Eigenschaft **Für COM\-Interop registrieren** finden Sie auf der Eigenschaftenseite **Erstellen** im Ordner Konfigurationseigenschaften.  
  
 Mögliche Ursachen für diesen Fehler:  
  
-   Aufheben der Registrierung der vorherigen Typbibliothek für die Assembly nicht möglich.  Hierbei kann es sich um ein Zugriffsproblem in der Registrierung handeln.  
  
-   Aufheben der Registrierung der alten Assembly nicht möglich.  Hierbei kann es sich auch um ein Zugriffsproblem in der Registrierung handeln.  
  
 Wenn die Aufhebung der Registrierung fehlschlägt, kann ein Verlust der GUID für **CoCreatable**\-Objekte sowie für jeden beliebigen Typ der Bibliotheks\-GUIDs auftreten.  Allerdings schlägt der gesamte Buildprozess nicht fehl.  
  
## Siehe auch  
 [COM Interoperability in .NET Framework Applications](/dotnet/visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications)