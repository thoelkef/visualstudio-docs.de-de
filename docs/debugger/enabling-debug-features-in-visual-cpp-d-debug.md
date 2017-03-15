---
title: "Aktivieren von Debugfeatures in Visual&#160;C++ (/D_DEBUG) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "/D_DEBUG (Compileroption) [C++]"
  - "_DEBUG-Makro"
  - "Assertionen, Aktivieren von Debugfeatures"
  - "D_DEBUG (Compileroption)"
  - "Debugbuilds, MFC"
  - "Debuggen [C++], Aktivieren von Debugfeatures"
  - "Debuggen [MFC], Aktivieren von Debugfeatures"
  - "MFC-Bibliotheken, Debugversion"
ms.assetid: 276e2254-7274-435e-ba4d-67fcef4f33bc
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Aktivieren von Debugfeatures in Visual&#160;C++ (/D_DEBUG)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Wenn Sie das Programm mit definiertem **\_DEBUG**\-Symbol kompilieren, aktivieren Sie damit die Debugfeatures in [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)], \(z. B. Assertionen\).  Sie können **\_DEBUG** auf zwei Arten definieren:  
  
-   Geben Sie im Quellcode **\#define \_DEBUG** an, oder  
  
-   Geben Sie die **\/D\_DEBUG**\-Compileroption an. \(Wenn Sie das Projekt in Visual Studio mit einem Assistenten erstellen, wird **\/D\_DEBUG** automatisch in der Debugkonfiguration definiert.\)  
  
 Wenn **\_DEBUG** definiert wird, kompiliert der Compiler Codeabschnitte, die in **\#ifdef \_DEBUG** und `#endif` eingeschlossen sind.  
  
 Die Debugkonfiguration eines MFC\-Programms muss mit einer Debugversion der MFC\-Bibliothek verknüpft werden.  Die korrekte MFC\-Bibliotheksversion, mit der verknüpft werden soll, wird auf der Grundlage der definierten Symbole, z. B. **\_DEBUG** und **\_UNICODE**, von den MFC\-Headerdateien bestimmt.  Einzelheiten dazu finden Sie unter [Versionen der MFC\-Bibliothek](/visual-cpp/mfc/mfc-library-versions).  
  
## Siehe auch  
 [Debuggen von systemeigenem Code](../debugger/debugging-native-code.md)   
 [Projekteinstellungen für eine C\+\+\-Debugkonfiguration](../debugger/project-settings-for-a-cpp-debug-configuration.md)