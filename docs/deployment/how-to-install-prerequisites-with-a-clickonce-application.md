---
title: "How to: Install Prerequisites with a ClickOnce Application | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "deploying applications [ClickOnce], prerequisites"
  - "prerequisites, ClickOnce"
  - "components, bootstrapping"
ms.assetid: e964fca5-fdfd-47cf-a1c9-7fb96b1c88b5
caps.latest.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 13
---
# How to: Install Prerequisites with a ClickOnce Application
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Alle [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendungen erfordern vor dem Ausführen die Installation der richtigen Version von .NET Framework. Viele Anwendungen benötigen zudem weitere Komponenten.  Beim Veröffentlichen einer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendung können Sie aus einem Satz erforderlicher Komponenten wählen, die mit der Anwendung als Paket veröffentlicht werden sollen.  Bei der Installation wird überprüft, ob die erforderlichen Komponenten bereits vorhanden sind. Andernfalls werden diese vor der [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendung installiert.  
  
 Anstatt die erforderlichen Komponenten als Paket zur Verfügung zu stellen, können Sie auch einen Downloadpfad für die Komponenten angeben.  Sie können beispielsweise anstelle der Paketveröffentlichung erforderlicher Komponenten mit jeder Anwendung eine zentrale Dateifreigabe oder ein Webverzeichnis verwenden, das die Installationsprogramme für alle erforderlichen Komponenten enthält. Die Komponenten werden bei der Installation von diesem Speicherort heruntergeladen und installiert.  
  
> [!IMPORTANT]
>  Sollten Sie erforderliche Installer\-Pakete auf dem Entwicklungscomputer vor dem Veröffentlichen Ihre erstes [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung.  Weitere Informationen finden Sie unter [How to: Include Prerequisites with a ClickOnce Application](../deployment/how-to-include-prerequisites-with-a-clickonce-application.md).  
  
 Erforderliche Komponenten werden im **Projekt\-Designer** im Bereich **Veröffentlichen** über das Dialogfeld **Erforderliche Komponenten** verwaltet.  
  
> [!NOTE]
>  Sie können auch eigene Komponenten zur festgelegten Liste erforderlicher Komponenten hinzufügen.  Weitere Informationen finden Sie unter [Erstellen von Bootstrapperpaketen](../deployment/creating-bootstrapper-packages.md).  
  
### So legen Sie die erforderlichen Komponenten für eine ClickOnce\-Anwendung fest  
  
1.  Wählen Sie im **Projektmappen\-Explorer** ein Projekt aus, und klicken Sie im Menü **Projekt** auf **Eigenschaften**.  
  
2.  Wählen Sie den Bereich **Veröffentlichen** aus.  
  
3.  Klicken Sie auf die Schaltfläche **Erforderliche Komponenten**, um das Dialogfeld **Erforderliche Komponenten** zu öffnen.  
  
4.  Stellen Sie im Dialogfeld **Erforderliche Komponenten** sicher, dass das Kontrollkästchen **Setupprogramm zur Installation erforderlicher Komponenten erstellen** aktiviert ist.  
  
5.  Markieren Sie in der Liste **Erforderliche Komponenten** die Komponenten, die Sie installieren möchten, und klicken Sie anschließend auf **OK**.  
  
     Die ausgewählten Komponenten werden zu einem Paket zusammengefasst und zusammen mit der Anwendung veröffentlicht.  
  
### So geben Sie einen anderen Downloadpfad für erforderliche Komponenten an  
  
1.  Wählen Sie im **Projektmappen\-Explorer** ein Projekt aus, und klicken Sie im Menü **Projekt** auf **Eigenschaften**.  
  
2.  Wählen Sie den Bereich **Veröffentlichen** aus.  
  
3.  Klicken Sie auf die Schaltfläche **Erforderliche Komponenten**, um das Dialogfeld **Erforderliche Komponenten** zu öffnen.  
  
4.  Stellen Sie im Dialogfeld **Erforderliche Komponenten** sicher, dass das Kontrollkästchen **Setupprogramm zur Installation erforderlicher Komponenten erstellen** aktiviert ist.  
  
5.  Wählen Sie im Bereich **Installationsort für erforderliche Komponenten angeben** die Option **Erforderliche Komponenten von folgendem Speicherort herunterladen** aus.  
  
6.  Wählen Sie in der Dropdownliste einen Speicherort aus, oder geben Sie eine URL, einen Dateipfad oder einen FTP\-Pfad ein. Klicken Sie anschließend auf **OK.**  
  
    > [!NOTE]
    >  Stellen Sie sicher, dass die Installationsprogramme für die ausgewählten Komponenten am angegebenen Speicherort vorhanden sind.  
  
## Siehe auch  
 [Publishing ClickOnce Applications](../deployment/publishing-clickonce-applications.md)   
 [How to: Publish a ClickOnce Application using the Publish Wizard](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)