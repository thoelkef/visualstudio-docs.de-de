---
title: "Typauflistungs-Editor (Dialogfeld) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "TypeCollectionEditor.UI"
ms.assetid: 63cdea6b-bca2-4c06-b8b4-c8faabd40726
caps.latest.revision: 4
caps.handback.revision: 4
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Typauflistungs-Editor (Dialogfeld)
Das Dialogfeld **Typauflistungs\-Editor** wird verwendet, um der **Send**\-Aktivität und der **Receive**\-Aktivität bekannte Typen hinzuzufügen.Dieses Dialogfeld wird auch verwendet, um der **InvokeMethod**\-Aktivität generische Typargumente hinzuzufügen.Wenn das Dialogfeld **Typauflistungs\-Editor** verwendet wird, um der **Send**\-Aktivität und der **Receive**\-Aktivität bekannte Typen hinzufügen, müssen die Typhinzufügungen hier eindeutig zu sein.Wenn ein doppelter Typ hinzugefügt und die Änderung durch Klicken auf **OK** bestätigt wird, wird eine Fehlermeldung zurückgegeben.Wenn das Dialogfeld **Typauflistungs\-Editor** verwendet wird, um der **InvokeMethod**\-Aktivität generische Typargumente hinzuzufügen, ist das Hinzufügen doppelter Typen zulässig.  
  
> [!NOTE]
>  [!INCLUDE[crabout](../test/includes/crabout_md.md)] zu bekannten Typen finden Sie unter [Bekannte Typen in Datenverträgen](../Topic/Data%20Contract%20Known%20Types.md).  
  
 In der folgenden Tabelle werden die Benutzeroberflächenelemente des Dialogfelds **Typauflistung** beschrieben.  
  
|Benutzeroberflächenelement|Beschreibung|  
|--------------------------------|------------------|  
|**Typenliste**|Eine Liste der Typen, die hinzugefügt oder entfernt wurden.|  
  
## So öffnen Sie den Typauflistungs\-Editor  
  
#### So öffnen Sie den Typauflistungs\-Editor für die Send\- und die Receive\-Aktivität  
  
1.  Wählen Sie die **Send**\-Aktivität oder die **Receive**\-Aktivität in der Entwurfsansicht aus.  
  
2.  Drücken Sie **F4**, um das Fenster **Eigenschaften** zu öffnen.  
  
3.  Klicken Sie im **Eigenschaftenfenster** neben der **KnownTypes**\-Eigenschaft auf die Schaltfläche mit den Auslassungszeichen \(...\).  
  
#### So öffnen Sie den Typauflistungs\-Editor für die InvokeMethod\-Aktivität  
  
1.  Wählen Sie die **InvokeMethod**\-Aktivität in der Entwurfsansicht aus.  
  
2.  Drücken Sie **F4**, um das Fenster **Eigenschaften** zu öffnen.  
  
3.  Klicken Sie im **Eigenschaftenfenster** neben der **GenericTypeArguments**\-Eigenschaft auf die Schaltfläche mit den Auslassungszeichen.