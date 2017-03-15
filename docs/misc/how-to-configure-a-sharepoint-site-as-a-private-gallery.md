---
title: "Gewusst wie: Konfigurieren einer SharePoint-Website als privaten Katalog | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Sharepoint, private Kataloge"
  - "Private Kataloge, Sharepoint"
ms.assetid: 6c6ed45f-7e46-4ed0-8b5c-839dbbe3769f
caps.latest.revision: 9
caps.handback.revision: 9
manager: "douge"
---
# Gewusst wie: Konfigurieren einer SharePoint-Website als privaten Katalog
Sie können eine SharePoint\-Listenseite erstellen, auf der Erweiterungen als privater Katalog beschrieben und bereitgestellt werden, und die Liste zu **Erweiterungen und Updates** hinzufügen. Weitere Informationen finden Sie unter [Private Galerien](../extensibility/private-galleries.md).  
  
 Gehen Sie wie folgt vor, um mit SharePoint einen privaten Katalog zu erstellen:  
  
1.  Erstellen Sie zuerst eine Listenseite für den privaten Katalog.  
  
2.  Laden Sie dann die Erweiterungsdateien \(VSIX\) als Elemente für die Listenseite hoch.  
  
> [!IMPORTANT]
>  Aus Sicherheitsgründen sind in SharePoint VSIX\-Dateien für das Hochladen gesperrt. Wenn Sie einen privaten Katalog einrichten, müssen Sie sicherstellen, dass die VSIX\-Dateien nicht gesperrt sind. Weitere Informationen finden Sie unter [Verwalten von gesperrten Dateitypen](http://go.microsoft.com/fwlink/?LinkID=201253).  
  
## Erstellen einer Listenseite für einen privaten Katalog  
 Abhängig von der Konfiguration der SharePoint\-Server, auf denen die Bereitstellung erfolgt, können die folgenden Schritte variieren. Im Allgemeinen gelten für alle SharePoint\-Erweiterungen \(WSP\) dieselben Bereitstellungsanweisungen. Eine Erläuterung des STSAdm\-Tools, das zum Verwalten von SharePoint\-Lösungsbereitstellungen verwendet werden kann, finden Sie auf der MSDN Magazine\-Website unter [Lösungsbereitstellung mit SharePoint 2007](http://go.microsoft.com/fwlink/?LinkId=220676).  
  
#### So erstellen Sie eine Listenseite für einen privaten Katalog  
  
1.  Laden Sie die Visual Studio\-Erweiterungen \(WSP\-Datei\) auf den SharePoint\-Server hoch.  
  
2.  Führen Sie an der Eingabeaufforderung die folgenden Befehle aus, um die WSP\-Datei auf dem SharePoint\-Server zu installieren.  
  
     **stsadm –o addsolution –name VisualStudioExtensionsList.wsp**  
  
     **stsadm –o deploysolution –name VisualStudioExtensionsList.wsp –url http:\/\/\<SERVERNAME\> –allowCasPolicies –allowgacdeployment –immediate**  
  
     Möglicherweise müssen Sie auch die Funktion über die SharePoint\-Benutzeroberfläche für eine Unterwebsite wie folgt aktivieren.  
  
    1.  Wählen Sie auf der Menüleiste die Optionen **Websiteaktionen**, **Websiteeinstellungen**, **Websitefeatures verwalten** aus.  
  
    2.  Wählen Sie die Schaltfläche **Aktivieren** \(neben **Visual Studio\-Erweiterungsbibliothek**\) aus.  
  
    3.  Fügen Sie die Visual Studio\-Erweiterungsbibliothek zur gewünschten Unterwebsite hinzu.  
  
 Wenn Sie eine Listenseite entfernen müssen, führen Sie die folgenden Schritte aus.  
  
#### So entfernen Sie eine Listenseite für einen privaten Katalog  
  
1.  Führen Sie an der Eingabeaufforderung die folgenden Befehle aus, um die WSP\-Datei auf dem SharePoint\-Server zu entfernen.  
  
     **stsadm –o retractsolution –name VisualStudioExtensionsList.wsp –immediate**  
  
     **stsadm –o deletesolution –name VisualStudioExtensionsList.wsp**  
  
2.  Ziehen Sie in SharePoint die Lösung zurück, und löschen Sie sie.  
  
## FAQ  
  
### Was geschieht, wenn eine Erweiterung hochgeladen wird?  
 Beim Hochladen einer Visual Studio\-Erweiterung \(VSIX\-Datei\) werden Informationen aus der Datei extrahiert. Zuerst werden einige Werte aus der eingebetteten VSIXMANIFEST\-Datei \(z. B. VsixId, VsixVersion usw.\) als ausgeblendete Metadatenwerte für das entsprechende SPListItem extrahiert und gespeichert. Dann werden die Symbol\- und PreviewImage\-Dateien für die Erweiterung in einer separaten Liste extrahiert und gespeichert.  
  
 Die Bilder werden in Bildbibliotheken namens "*Listentitel*\_VSIXIcons" und "*Listentitel*\_VSIXPreviewImages" gespeichert, wobei *Listentitel* der Name der Listeninstanz ist, in der die VSIX\-Dateien gespeichert werden. Dem Namen jeder Bilddatei wird die entsprechende VSIX\-ID als Präfix vorangestellt.  
  
### Was geschieht, wenn eine Erweiterung gelöscht wird?  
 Wenn eine VSIX\-Datei gelöscht wird, werden die entsprechenden Bilddateien \(sofern vorhanden\) ebenfalls gelöscht.  
  
### Was geschieht, wenn eine Erweiterung aktualisiert wird?  
 Eine Erweiterung kann durch Hochladen einer neuen Version der VSIX\-Datei und durch Überschreiben der vorhandenen Version aktualisiert werden. Wenn eine Erweiterung aktualisiert wird, werden alle Metadatenwerte und Bilder für die Erweiterung gemäß den Werten in der neuen Version aktualisiert.  
  
### Was geschieht, wenn eine Liste gelöscht wird?  
 Wenn eine Instanz einer Visual Studio\-Erweiterungsliste gelöscht wird, werden die entsprechenden "\_VSIXIcons"\- und "\_VSIXPreviewImages"\-Bildbibliotheken ebenfalls gelöscht.  
  
### Welche Versionen von SharePoint werden unterstützt?  
 Derzeit wird nur SharePoint 2010 unterstützt.  
  
## Siehe auch  
 [Private Galerien](../extensibility/private-galleries.md)