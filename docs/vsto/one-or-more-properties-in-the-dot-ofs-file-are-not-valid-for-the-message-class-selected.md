---
title: "Mindestens eine Eigenschaft in der OFS-Datei ist f&#252;r die ausgew&#228;hlte Nachrichtenklasse ung&#252;ltig | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VSTO.NewFormRegionWizard.OFSPropertyError"
dev_langs: 
  - "VB"
  - "CSharp"
ms.assetid: ca9e2ec1-df96-45ca-9611-cec47edfe1e4
caps.latest.revision: 8
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 7
---
# Mindestens eine Eigenschaft in der OFS-Datei ist f&#252;r die ausgew&#228;hlte Nachrichtenklasse ung&#252;ltig
  Dieser Fehler wird angezeigt, wenn Sie einen Formularbereich importieren, der in Outlook entworfen wurde, aber ein oder mehrere Felder im Formularbereich enthält, die mit den „message“\-Klassen nicht kompatibel sind, die Sie auf der letzten Seite des Assistenten **Neuer Formularbereich** auswählen.  
  
 Beispielsweise können Sie **Aufgabe \(IPM.Task\)** auf der letzten Seite des Assistenten **Neuer Formularbereich** auswählen. Wenn der Formularbereich ein Feld für die **Geschäftsadresse** enthält, wird dieser Fehler angezeigt, da eine Aufgabe keine Geschäftsadresse besitzt. Aus diesem Grund ist das Feld **Geschäftsadresse** nicht mit der „IPM.Task“\-Nachrichtenklasse kompatibel.  
  
### So beheben Sie diesen Fehler  
  
-   Auf der letzten Seite des Assistenten **Neuer Formularbereich** wählen Sie eine Nachrichtenklasse aus, die mit den Feldern im Formularbereich kompatibel ist.  
  
-   Entfernen Sie im Formulardesigner in Outlook Felder, die nicht mit den Nachrichtenklassen kompatibel sind, die Sie planen, auf der letzten Seite des Assistenten **Neuer Formularbereich** auszuwählen.  
  
## Siehe auch  
 [Exemplarische Vorgehensweise: Importieren eines in Outlook entworfenen Formularbereichs](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)  
  
  