---
title: "Gewusst wie: Herstellen einer Verbindung mit Daten in einem Dienst | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "Daten [Visual Studio], Verbinden mit Webdiensten"
  - "Daten [Visual Studio], Lesen aus Webdiensten"
  - "Datenquellen, Erstellen aus Webdiensten"
  - "Lesen von Daten, aus Webdiensten"
  - "Webdienste, Als Datenquellen"
  - "Webdienste, Verbindung herstellen"
  - "Webdienste, Lesen von Daten"
ms.assetid: a6b54353-05fe-4e5c-8631-90231fc95504
caps.latest.revision: 32
caps.handback.revision: 30
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Gewusst wie: Herstellen einer Verbindung mit Daten in einem Dienst
Sie können eine Verbindung zwischen der Anwendung und den von einem Dienst zurückgegebenen Daten herstellen, indem Sie den [Assistent zum Konfigurieren von Datenquellen](../data-tools/media/data-source-configuration-wizard.png) ausführen und auf der Seite **Datenquellentyp auswählen** die Option **Dienst** auswählen.  
  
 Bei Beendigung des Assistenten wird Ihrem Projekt ein Dientstverweis hinzugefügt, der sofort im [Datenquellenfenster](../Topic/Data%20Sources%20Window.md) verfügbar ist.  
  
> [!NOTE]
>  Die im Fenster **Datenquellen** angezeigten Elemente hängen von den vom Dienst zurückgegebenen Informationen ab.  Einige Dienste stellen möglicherweise nicht genügend Informationen bereit, damit der **Assistent zum Konfigurieren von Datenquellen** bindbare Objekte erstellen kann.  Wenn der Dienst beispielsweise ein nicht typisiertes Dataset zurückgibt, werden beim Beenden des Assistenten im Datenquellenfenster keine Elemente angezeigt.  Dies ist darauf zurückzuführen, dass nicht typisierte Datasets kein Schema bereitstellen, sodass der Assistent nicht über genügend Informationen zum Erstellen der Datenquelle verfügt.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
### So stellen Sie eine Verbindung zwischen der Anwendung und einem Dienst her  
  
1.  Klicken Sie im Menü **Daten** auf **Neue Datenquelle hinzufügen**.  
  
2.  Wählen Sie auf der Seite **Datenquellentyp auswählen** die Option **Dienst** aus, und klicken Sie dann auf **Weiter**.  
  
3.  Geben Sie die Adresse des Diensts ein, die Sie verwenden möchten, oder klicken Sie auf **Ermitteln**, um Dienste in der aktuellen Projektmappe zu suchen, und klicken Sie dann auf **Gehe zu**.  
  
4.  Optional kann ein neuer **Namespace** anstelle des Standardwerts eingegeben werden.  
  
    > [!NOTE]
    >  Klicken Sie auf **Erweitert**, um das [Dialogfeld "Dienstverweis konfigurieren"](../data-tools/configure-service-reference-dialog-box.md) zu öffnen.  
  
5.  Klicken Sie auf **OK**, um einen Dienstverweis auf das Projekt hinzuzufügen.  
  
6.  Klicken Sie auf **Fertig stellen**.  
  
     Die Datenquelle wird dem **Datenquellenfenster** hinzugefügt.  
  
## Nächste Schritte  
  
#### So fügen Sie der Anwendung Funktionalität hinzu  
  
-   Wählen Sie im **Datenquellenfenster** ein Element aus, und ziehen Sie es in ein Formular, um gebundene Steuerelemente zu erstellen.  Weitere Informationen finden Sie unter [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).  
  
## Siehe auch  
 [Exemplarische Vorgehensweise: Binden von WPF\-Steuerelementen an einen WCF\-Datendienst](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md)   
 [Exemplarische Vorgehensweise: Binden von Silverlight\-Steuerelementen an einen WCF\-Datendienst](../Topic/Walkthrough:%20Binding%20Silverlight%20Controls%20to%20a%20WCF%20Data%20Service.md)   
 [Windows Communication Foundation Services and WCF Data Services in Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)