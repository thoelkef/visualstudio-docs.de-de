---
title: "Walkthrough: Downloading Satellite Assemblies on Demand with the ClickOnce Deployment API Using the Designer | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
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
  - "Windows Forms, globalization"
  - "ClickOnce deployment, globalization"
  - "localization, Windows Forms"
  - "ClickOnce, on-demand download"
  - "Windows Forms, localization"
  - "ClickOnce deployment, localization"
  - "walkthroughs, localization"
ms.assetid: 82b85a47-b223-4221-a17c-38a52c3fb6e2
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Walkthrough: Downloading Satellite Assemblies on Demand with the ClickOnce Deployment API Using the Designer
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Mit Windows Forms\-Anwendungen können mehrere Kulturen mithilfe von Satellitenassemblys konfiguriert werden.  Eine *Satellitenassembly* ist eine Assembly, die Anwendungsressourcen für eine andere Kultur als die Standardkultur der Anwendung enthält.  
  
 Wie in [Localizing ClickOnce Applications](../deployment/localizing-clickonce-applications.md) erläutert können Sie mehrere Satellitenassemblys für mehrere Kulturen innerhalb derselben [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Bereitstellung einschließen.  In der Standardeinstellung lädt [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] alle Satellitenassemblys in Ihrer Bereitstellung auf den Clientcomputer herunter, obwohl ein einzelner Client wahrscheinlich nur eine Satellitenassembly benötigt.  
  
 Diese exemplarische Vorgehensweise beschreibt, wie Sie Ihre Satellitenassemblys als optional kennzeichnen und nur die Assembly herunterladen, die ein Clientcomputer für die eigenen aktuellen Kultureinstellungen benötigt.  
  
> [!NOTE]
>  Zu Testzwecken legen die folgenden Codebeispiele die Kultur programmgesteuert auf `ja-JP` fest.  Im Abschnitt "Nächste Schritte" weiter unten in diesem Thema finden Sie Informationen zum Anpassen dieses Codes für eine Produktionsumgebung.  
  
### So markieren Sie Satellitenassemblys als optional  
  
1.  Erstellen Sie das Projekt.  Dadurch werden Satellitenassemblys für alle Kulturen generiert, die Sie lokalisieren.  
  
2.  Klicken Sie im Projektmappen\-Explorer mit der rechten Maustaste auf den Projektnamen, und klicken Sie dann auf **Eigenschaften**.  
  
3.  Klicken Sie auf die Registerkarte **Veröffentlichen**, und klicken Sie dann auf die **Anwendungsdateien**.  
  
4.  Aktivieren Sie das Kontrollkästchen **Alle Dateien anzeigen**, um Satellitenassemblys anzuzeigen.  Standardmäßig werden alle Satellitenassemblys in Ihre Bereitstellung aufgenommen und in diesem Dialogfeld angezeigt.  
  
     Eine Satellitenassembly hat einen Namen im Format *isoCode*\\ApplicationName.Resources.dll, wobei *isoCode* eine Sprach\-ID im RFC 1766\-Format ist.  
  
5.  Klicken Sie auf **Neu** in der Liste **Downloadgruppe** für jede Sprach\-ID.  Wenn Sie zur Eingabe eines Downloadgruppennamens aufgefordert werden, geben Sie die Sprach\-ID ein.  Geben Sie z. B. für eine japanische Satellitenassembly den Downloadgruppennamen `ja-JP` an.  
  
6.  Schließen Sie das Dialogfeld **Anwendungsdateien**.  
  
### So laden Sie Satellitenassemblys bei Bedarf in C\# herunter  
  
1.  Öffnen Sie die Datei "Program.cs".  Wenn diese Datei nicht im Projektmappen\-Explorer angezeigt wird, wählen Sie das Projekt aus, und klicken Sie im Menü **Projekt** auf **Alle Dateien anzeigen**.  
  
2.  Verwenden Sie den folgenden Code, um die entsprechende Satellitenassembly herunterzuladen und die Anwendung zu starten.  
  
     [!code-cs[ClickOnce.SatelliteAssemblies#1](../deployment/codesnippet/CSharp/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer_1.cs)]  
  
### So laden Sie Satellitenassemblys bei Bedarf in Visual Basic herunter  
  
1.  Klicken Sie im Fenster **Eigenschaften** der Anwendung auf die Registerkarte **Anwendung**.  
  
2.  Klicken Sie unten auf der Registerkarte auf **Anwendungsereignisse anzeigen**.  
  
3.  Fügen Sie folgenden Importanweisungen am Anfang der Datei "ApplicationEvents.VB" hinzu.  
  
     [!code-vb[ClickOnce.SatelliteAssembliesVB#1](../deployment/codesnippet/VisualBasic/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer_2.vb)]  
  
4.  Fügen Sie der `MyApplication`\-Klasse folgenden Code hinzu.  
  
     [!code-vb[ClickOnce.SatelliteAssembliesVB#2](../deployment/codesnippet/VisualBasic/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer_3.vb)]  
  
## Nächste Schritte  
 In einer Produktionsumgebung müssen Sie wahrscheinlich die Zeile in den Codebeispielen entfernen, die <xref:System.Threading.Thread.CurrentUICulture%2A> auf einen bestimmten Wert festlegt, da auf Clientcomputern der richtige Wert standardmäßig festgelegt ist.  Beim Ausführen der Anwendung auf einem japanischen Clientcomputer ist <xref:System.Threading.Thread.CurrentUICulture%2A> z. B. standardmäßig `ja-JP`.  Das programmgesteuerte Festlegen ist eine gute Möglichkeit, die Satellitenassemblys zu testen, bevor Sie die Anwendung bereitstellen.  
  
## Siehe auch  
 [Walkthrough: Downloading Satellite Assemblies on Demand with the ClickOnce Deployment API](../deployment/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api.md)   
 [Localizing ClickOnce Applications](../deployment/localizing-clickonce-applications.md)