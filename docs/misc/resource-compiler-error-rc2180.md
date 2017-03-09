---
title: "Ressourcencompiler: Fehler RC2180 | Microsoft Docs"
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
  - "RC2180"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RC2180"
ms.assetid: 6d296138-7989-491e-a45b-6c3a4743116a
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# Ressourcencompiler: Fehler RC2180
Fehler beim Öffnen einer temporären Datei  
  
 Der Ressourcencompiler\/Visual C\+\+ konnte eine temporäre Datei nicht öffnen. Die wahrscheinlichste Ursache ist, dass Sie nicht über Schreibberechtigungen für das Verzeichnis verfügen oder dass das Verzeichnis nicht vorhanden ist. Der Ressourcencompiler\/Visual C\+\+ versucht, diese Dateien im von der **TMP**\-Umgebungsvariablen angegebenen Verzeichnis bzw. im aktuellen Verzeichnis zu verwenden, wenn kein Verzeichnis angegeben ist.