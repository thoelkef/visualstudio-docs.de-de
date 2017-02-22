---
title: "Problembehandlung bei Codeausschnitten | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IntelliSense-Codeausschnitte, Problembehandlung"
  - "Problembehandlung (IntelliSense-Codeausschnitte)"
  - "Problembehandlung in Visual Basic, IntelliSense-Codeausschnitte"
ms.assetid: 7b6dd40e-2f78-4b50-8e68-41fac1bcb81e
caps.latest.revision: 17
caps.handback.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Problembehandlung bei Codeausschnitten
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Für Probleme mit IntelliSense\-Codeausschnitten gibt es in der Regel zwei Ursachen: eine beschädigte Ausschnittdatei oder fehlerhafter Inhalt in der Ausschnittdatei.  
  
## Allgemeine Probleme  
  
### Der Ausschnitt kann nicht gezogener Explorer in eine Visual Studio\-Quelldatei von Datei sein  
  
-   Der XML\-Code in der Ausschnittdatei ist möglicherweise beschädigt.  Der **XML\-Editor** in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] kann nach Problemen in der XML\-Struktur suchen.  
  
-   Die Ausschnittdatei entspricht eventuell nicht dem Ausschnittschema.  Der **XML\-Editor** in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] kann nach Problemen in der XML\-Struktur suchen.  
  
### Der Code enthält Compilerfehler, die nicht hervorgehoben werden  
  
-   Möglicherweise fehlt ein Projektverweis.  Lesen Sie die Dokumentation zum Codeausschnitt.  Wenn der Verweis auf dem Computer nicht gefunden wird, müssen Sie ihn installieren.  Durch Einfügen eines Ausschnitts sollten auch alle benötigten Verweise zu dem Projekt hinzugefügt werden.  Wenn der Ausschnitt die Verweisinformationen nicht enthält, wird dies dem Ausschnittersteller unter Umständen als Fehler mitgeteilt.  
  
-   Eine Variable ist eventuell nicht definiert.  Nicht definierte Variablen in einem Ausschnitt sollten hervorgehoben werden.  Andernfalls wird dem Ausschnittersteller möglicherweise ein Fehler gemeldet.  
  
## Siehe auch  
 [Codeausschnitte](../ide/code-snippets.md)