---
title: "Diese Aufgabe erfordert zus&#228;tzliche Rechte | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.UACDialog"
ms.assetid: a03d3509-5e6e-411a-9aec-0766d7ee3a0e
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Diese Aufgabe erfordert zus&#228;tzliche Rechte
Dieser Fehler wird angezeigt, wenn ein Visual Studio\-Befehl von einem Benutzer aufgerufen wird, dessen Konto nicht genügend Berechtigungen verfügt, den Vorgang abzuschließen.  
  
 Einige Visual Studio\-Befehle müssen mit einem Konto ausgeführt werden, das über ausreichende Benutzerzugriffsrechte verfügt, um sind, den Befehl zu aktivieren, alle erforderlichen Dateien und Registrierungsschlüssel zu lesen oder zu schreiben.  Um diese Berechtigungen zu erhalten, müssen Sie Visual Studio mit einem Konto das Zugriff erhöht hat, wie ein Administrator schließen und erneut öffnen.  
  
 Weitere Informationen zu Berechtigungen, wenn Sie Visual Studio ausführen, finden Sie unter [Benutzerberechtigungen](../ide/user-permissions-and-visual-studio.md).  
  
### So beheben Sie diesen Fehler  
  
1.  Klicken Sie im Dialogfeld auf **Neustart unter anderem Konto**.  
  
     Dadurch werden Sie aufgefordert, die aktuell geladene Projektmappe zu speichern und dann enthält Visual Studio und neu gestartet und Sie werden aufgefordert, zu einem anderen Konto zu wechseln.  
  
2.  Melden Sie sich bei der Anmeldeaufforderung unter einem Konto an, das mehr Berechtigungen als das zuvor verwendete Konto aufweist, beispielsweise unter dem Administratorkonto.  
  
     Wenn beginnt, wird die letzte Projektmappe und die Befehlszeile erneut geladen wird.  
  
> [!NOTE]
>  Die Anmeldung mit einem Konto, das mehr Berechtigungen aufweist, nicht unbedingt gewährleistet, dass der Visual Studio\-Befehl funktioniert.  Einige Befehle können selbst ausgeführt, wenn Sie ein Administratorkonto verwenden.