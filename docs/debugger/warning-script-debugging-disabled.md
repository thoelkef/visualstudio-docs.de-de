---
title: "Warnung: Skriptdebuggen deaktiviert | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.scriptdisabled"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: 323d2b1d-52a4-42f7-b4ad-96b4b0c23b8d
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Warnung: Skriptdebuggen deaktiviert
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Skriptdebuggen ist in Internet Explorer derzeit deaktiviert  
  
 Diese Warnung wird ausgegeben, wenn Sie versuchen, Skripts zu debuggen, ohne dass Skriptdebuggen in Internet Explorer aktiviert ist.  Das Skriptdebuggen ist in Internet Explorer aus Sicherheitsgründen standardmäßig deaktiviert.  
  
### So aktivieren Sie das Skriptdebuggen in Internet Explorer  
  
1.  Wählen Sie in Internet Explorer im Menü **Extras** die Option **Internetoptionen** aus.  
  
2.  Klicken Sie im Dialogfeld **Internetoptionen** auf die Registerkarte **Erweitert**.  
  
3.  Zeigen Sie auf der Registerkarte **Erweitert** unter der Kategorie **Browsen** das Feld **Einstellungen** an.  
  
4.  Deaktivieren Sie **Skriptdebugging deaktivieren \(Internet Explorer\)**.  
  
5.  Klicken Sie auf **OK**.  
  
6.  Beenden Sie Internet Explorer, und starten Sie die Anwendung neu.  
  
     Die neuen Einstellungen sind jetzt wirksam.  
  
## Siehe auch  
 [Gewusst wie: Anfügen an ein Skript](../debugger/how-to-attach-to-script.md)