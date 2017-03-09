---
title: "Diese Einzelinstanzanwendung konnte keine Verbindung zur urspr&#252;nglichen Instanz herstellen. | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbrAppModel_SingleInstanceCantConnect"
ms.assetid: 7c2c0cee-02a1-4157-be03-39d18e18408f
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Diese Einzelinstanzanwendung konnte keine Verbindung zur urspr&#252;nglichen Instanz herstellen.
Diese Einzelinstanzanwendung konnte keine Verbindung zur ursprünglichen Instanz herstellen. Mögliche Ursachen für dieses Problem:  
  
-   Die ursprüngliche Instanz reagiert nicht mehr.  
  
-   Die Anwendung verfügt nicht über die Berechtigungen, Kernelobjekte zu erstellen. Weitere Informationen zu Kernelobjekten finden Sie unter [Mutexes](../Topic/Mutexes.md).  
  
     Der Basisname des Kernelobjekts wird gebildet, indem GUID, Hauptversionsnummer und Nebenversionsnummer der Assembly aneinander gehängt werden. Der Basisname könnte beispielsweise `3639f15d-9547-43da-8145-60da347829915.1` lauten.  
  
### So beheben Sie diesen Fehler beim Entwickeln der Anwendung  
  
1.  Stellen Sie sicher, dass die Anwendung nicht in einen nicht reagierenden Zustand versetzt wird.  
  
2.  Stellen Sie sicher, dass die Anwendung über ausreichende Berechtigungen verfügt, um Kernelobjekte zu erstellen.  
  
3.  Starten Sie die ursprüngliche Instanz der Anwendung neu.  
  
4.  Starten Sie den Computer neu, um alle Prozesse zu beenden, die möglicherweise die Ressource verwenden, die für eine Verbindung zur ursprünglichen Instanzanwendung erforderlich ist.  
  
5.  Notieren Sie sich die Umstände, unter denen der Fehler aufgetreten ist, und wenden Sie sich an den Produktsupport von Microsoft.  
  
## Siehe auch  
 [NICHT IM BUILD: Angeben des Instanziierungsverhaltens für eine Anwendung \(Visual Basic\)](http://msdn.microsoft.com/de-de/48539ad8-d960-4210-beab-ee65f6c6dc6e)   
 [Debugger – Grundlagen](../debugger/debugger-basics.md)   
 [PAVEOVER Produktsupport und Barrierefreiheit](http://msdn.microsoft.com/de-de/14e1d293-7b6d-40a6-bf3e-a92f8ee6c88c)