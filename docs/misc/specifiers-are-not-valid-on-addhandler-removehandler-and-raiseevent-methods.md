---
title: "Spezifizierer sind f&#252;r AddHandler-, RemoveHandler- und RaiseEvent-Methoden nicht zul&#228;ssig. | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc31135"
  - "bc31135"
helpviewer_keywords: 
  - "BC31135"
ms.assetid: 2eaf5a6f-d201-4f9b-bcdf-12170cb44791
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Spezifizierer sind f&#252;r AddHandler-, RemoveHandler- und RaiseEvent-Methoden nicht zul&#228;ssig.
Die Methodendeklarationen `AddHandler`, `RemoveHandler` und `RaiseEvent` können nicht mit Schlüsselwörtern wie `Public` oder `ReadOnly` geändert werden. Nur veränderbare Deklarationen dürfen solche Schlüsselwörter enthalten.  
  
 **Fehler\-ID:** BC31135  
  
### So beheben Sie diesen Fehler  
  
-   Entfernen Sie das Schlüsselwort aus der Methodendeklaration.  
  
## Siehe auch  
 [Event Statement](/dotnet/visual-basic/language-reference/statements/event-statement)   
 [AddHandler – löschen](http://msdn.microsoft.com/de-de/fc464cf8-582c-48a6-a9c2-185c4c3d5ff8)   
 [RemoveHandler – löschen](http://msdn.microsoft.com/de-de/35c17f61-6e22-4b87-b6e1-3ed0c27a88a0)   
 [RaiseEvent – löschen](http://msdn.microsoft.com/de-de/7f765da0-5491-40b6-9ed5-24c98f9daad9)   
 [NIB: Schlüsselwörter &#91;Visual Basic&#93;](http://msdn.microsoft.com/de-de/3a6fda51-6ade-4862-a407-1c305c3906ec)   
 [Events](/dotnet/visual-basic/programming-guide/language-features/events/events)