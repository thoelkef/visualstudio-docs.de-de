---
title: "Projektbuildfehler PRJ0039 | Microsoft Docs"
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
  - "PRJ0039"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "PRJ0039"
ms.assetid: 207bbc28-922f-44d6-8bdd-3016c850f5b9
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# Projektbuildfehler PRJ0039
Eine temporäre Datei kann nicht erstellt werden. Dies ist erforderlich, damit das NMake\-Tool ausgeführt werden kann.  
  
 Beim Erstellen eines Makefile\-Projekts \(siehe [Erstellen eines Makefile\-Projekts](/visual-cpp/ide/creating-a-makefile-project)\), muss das Visual C\+\+\-Projektsystem einige temporäre Dateien erstellen. Dieser Fehler weist darauf hin, dass das Projektsystem eine oder mehrere dieser Dateien nicht erstellen konnte.  
  
 Die TMP\-Umgebungsvariable enthält den Namen des temp\-Verzeichnisses.  
  
 Mögliche Ursachen für diesen Fehler und Vorschläge zur Lösung sind unten aufgeführt:  
  
 Der Benutzer besitzt keinen Schreibzugriff auf das temp\-Verzeichnis  
 Überprüfen Sie, ob Sie Schreibzugriff auf das temp\-Verzeichnis haben.  
  
 Zu viele temporäre Dateien im temp\-Verzeichnis  
 Möglicherweise haben andere Prozesse temporäre Dateien erstellt, die sie nicht gelöscht haben. Löschen Sie einige oder alle dieser temporären Dateien.  
  
 Es ist kein freier Speicherplatz verfügbar  
 Löschen Sie einige Dateien auf dem Datenträger, oder verschieben Sie Ihr temporäres Verzeichnis auf einen Datenträger mit verfügbarem Speicherplatz.  
  
 Die TMP\-Umgebungsvariable ist ungültig  
 Möglicherweise verweist die TMP\-Umgebungsvariable auf ein Verzeichnis, das nicht vorhanden ist.