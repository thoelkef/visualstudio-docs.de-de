---
title: "Walkthrough: Downloading Satellite Assemblies on Demand with the ClickOnce Deployment API | Microsoft Docs"
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
  - "ClickOnce deployment, globalization"
  - "localization, Windows Forms"
  - "Windows Forms, localization"
  - "globalization, ClickOnce"
  - "satellite assemblies, ClickOnce"
  - "ClickOnce deployment, on-demand download"
  - "localization, ClickOnce deployment"
  - "ClickOnce deployment, localization"
ms.assetid: fdaa553f-a27e-44eb-a4e2-08c122105a87
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Walkthrough: Downloading Satellite Assemblies on Demand with the ClickOnce Deployment API
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Mit Windows Forms\-Anwendungen können mehrere Kulturen mithilfe von Satellitenassemblys konfiguriert werden. Eine *Satellitenassembly* ist eine Assembly, die Anwendungsressourcen für eine andere Kultur als die Standardkultur der Anwendung enthält.  
  
 Wie in [Localizing ClickOnce Applications](../deployment/localizing-clickonce-applications.md) erläutert können Sie mehrere Satellitenassemblys für mehrere Kulturen innerhalb derselben [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Bereitstellung einschließen. In der Standardeinstellung lädt [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] alle Satellitenassemblys in Ihrer Bereitstellung auf den Clientcomputer herunter, obwohl ein einzelner Client wahrscheinlich nur eine Satellitenassembly benötigt.  
  
 Diese exemplarische Vorgehensweise beschreibt, wie Sie Ihre Satellitenassemblys als optional kennzeichnen und nur die Assembly herunterladen, die ein Clientcomputer für die eigenen aktuellen Kultureinstellungen benötigt. Im nachfolgend dargestellten Verfahren werden die im [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)] verfügbaren Tools verwendet. Sie können diese Aufgabe auch in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ausführen.  Siehe auch [Exemplarische Vorgehensweise: Bedarfsgerechtes Herunterladen von Satellitenassemblys mit der API für die ClickOnce\-Bereitstellung unter Verwendung des Designers](http://msdn.microsoft.com/library/ms366788\(v=vs.110\)) oder [Exemplarische Vorgehensweise: Bedarfsgerechtes Herunterladen von Satellitenassemblys mit der API für die ClickOnce\-Bereitstellung unter Verwendung des Designers](http://msdn.microsoft.com/library/ms366788\(v=vs.120\)).  
  
> [!NOTE]
>  In den folgenden Codebeispielen wird die Kultur zu Testzwecken programmgesteuert auf `ja-JP` festgelegt. Im Abschnitt "Nächste Schritte" weiter unten in diesem Thema finden Sie Informationen zum Anpassen dieses Codes für eine Produktionsumgebung.  
  
## Vorbereitungsmaßnahmen  
 In diesem Thema wird davon ausgegangen, dass Sie wissen, wie der Anwendung mit Visual Studio lokalisierte Ressourcen hinzugefügt werden können. Ausführliche Anweisungen dazu finden Sie unter [Exemplarische Vorgehensweise: Lokalisieren von Windows Forms](https://msdn.microsoft.com/en-us/library/vstudio/y99d1cd3\(v=vs.100\).aspx).  
  
### So laden Sie Satellitenassemblys bei Bedarf herunter  
  
1.  Fügen Sie den folgenden Code der Anwendung hinzu, um das bedarfsabhängige Herunterladen von Satellitenassemblys zu aktivieren.  
  
     [!code-cs[ClickOnce.SatelliteAssembliesSDK#1](../deployment/codesnippet/CSharp/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api_1.cs)]
     [!code-vb[ClickOnce.SatelliteAssembliesSDK#1](../deployment/codesnippet/VisualBasic/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api_1.vb)]  
  
2.  Generieren Sie mit [Resgen.exe \(Resource File Generator\)](../Topic/Resgen.exe%20\(Resource%20File%20Generator\).md) oder [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Satellitenassemblys für Ihre Anwendung.  
  
3.  Generieren Sie ein Anwendungsmanifest, oder öffnen Sie das vorhandene Anwendungsmanifest, indem Sie MageUI.exe verwenden. Weitere Informationen zu diesem Tool finden Sie unter [MageUI.exe \(Manifest Generation and Editing Tool, Graphical Client\)](../Topic/MageUI.exe%20\(Manifest%20Generation%20and%20Editing%20Tool,%20Graphical%20Client\).md).  
  
4.  Klicken Sie auf die Registerkarte **Dateien**.  
  
5.  Klicken Sie auf die Schaltfläche mit den **Auslassungszeichen** \(**...**\), und wählen Sie das Verzeichnis aus, das alle Assemblys und Dateien der Anwendung enthält, einschließlich der Satellitenassemblys, die Sie mit Resgen.exe generiert haben. \(Der Name einer Satellitenassembly hat folgendes Format: *ISO\-Code*\\Anwendungsname.resources.dll. Dabei entspricht *ISO\-Code* einem Sprachenbezeichner im Format RFC 1766.\)  
  
6.  Klicken Sie auf **Auffüllen**, um die Dateien zu Ihrer Bereitstellung hinzuzufügen.  
  
7.  Aktivieren Sie für jede Satellitenassembly das Kontrollkästchen **Optional**.  
  
8.  Legen Sie für das Gruppenfeld jeder Satellitenassembly ihren ISO\-Sprachenbezeichner fest. Für eine japanische Satellitenassembly würden Sie beispielsweise den Downloadgruppennamen `ja-JP` angeben. Damit kann der Code, den Sie in Schritt 1 hinzugefügt haben, je nach der Einstellung der <xref:System.Threading.Thread.CurrentUICulture%2A>\-Benutzereigenschaft die entsprechende Satellitenassembly herunterladen.  
  
## Nächste Schritte  
 In einer Produktionsumgebung müssen Sie im Codebeispiel wahrscheinlich die Zeile entfernen, die für <xref:System.Threading.Thread.CurrentUICulture%2A> einen bestimmten Wert festlegt, denn auf Clientcomputern ist standardmäßig der richtige Wert festgelegt. Beim Ausführen der Anwendung auf einem japanischen Clientcomputer ist <xref:System.Threading.Thread.CurrentUICulture%2A> z. B. standardmäßig `ja-JP`. Diesen Wert programmgesteuert festzulegen bietet eine gute Möglichkeit zum Testen Ihrer Satellitenassemblys, bevor Sie Ihre Anwendung bereitstellen.  
  
## Siehe auch  
 [Localizing ClickOnce Applications](../deployment/localizing-clickonce-applications.md)