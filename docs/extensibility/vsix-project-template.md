---
title: "VSIX-Projektvorlage | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Bereitstellen von Paketen"
  - "Veröffentlichen der Erweiterung"
ms.assetid: b6c82167-e2a5-4cff-8c8b-2d72e2a9092c
caps.latest.revision: 21
caps.handback.revision: 21
ms.author: "gregvanl"
manager: "ghogen"
---
# VSIX-Projektvorlage
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie können die VSIX\-Projektvorlage verwenden, um eine oder mehrere Visual Studio\-Erweiterungen in einem VSIX\-Projekt zu umschließen und veröffentlichen Sie das Paket auf den [Visual Studio Gallery](http://go.microsoft.com/fwlink/?LinkID=123847) Website.  
  
 VSPackages, Assemblys, MEF\-Komponenten, Projektvorlagen, Elementvorlagen, Toolbox\-Steuerelemente und benutzerdefinierte Erweiterungstypen die VSIX\-Bereitstellung unterstützt.  
  
> [!NOTE]
>  Um VSIX\-Projekten verwenden zu können, müssen Sie das Visual Studio SDK installieren. Weitere Informationen über das Visual Studio SDK finden Sie unter [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## Wo finden Sie die VSIX\-Projektvorlage  
 Die VSIX\-Projektvorlage ist verfügbar in der **Neues Projekt** \(Dialogfeld\). Erweitern Sie entweder die **Visual Basic** Knoten oder **Visual C\#\-** Knoten, und wählen Sie dann **Erweiterbarkeit**.  
  
> [!TIP]
>  Sie sollten sicherstellen, dass diese .NET Framework 4.5 oder höher angegeben ist, in der Dropdownliste am oberen Rand der **Neues Projekt** \(Dialogfeld\).  
  
## Verwendet die VSIX\-Projektvorlage  
 Die VSIX\-Projektvorlage verfügt über zwei Hauptanwendungsgebiete:  
  
-   Bereitstellen von Projektvorlagen, Elementvorlagen und anderen Erweiterungen, die VSIX\-Unterstützung noch nicht installiert haben.  
  
-   Um die Ausgaben des mehrere Erweiterungen in ein Bereitstellungspaket zu umschließen.  
  
 Sie müssen nicht die VSIX\-Projektvorlage verwenden zum Bereitstellen von VSPackages oder andere Arten von Erweiterungen, die bereits VSIX unterstützen.  
  
## Verpacken einer Erweiterung in ein leeres VSIX\-Projekt  
 Sie können eine vorhandene Erweiterung oder eine Erweiterung, die VSIX\-Unterstützung durch Einbinden in ein leeres VSIX\-Projekt noch nicht verpacken. Die Erweiterung eingeschlossen werden, muss ein Typ, der von unterstützt wird die [VSIX\-Schema](../extensibility/vsix-extension-schema-2-0-reference.md).  
  
#### So verpacken Sie die Erweiterung mithilfe eines VSIX\-Projekts  
  
1.  Erstellen Sie die Projekte, die Ihre Erweiterung bilden.  
  
2.  Erstellen Sie ein VSIX\-Projekt mithilfe der **VSIX\-Projekt** Vorlage.  
  
     Source.Extension.vsixmanifest öffnet im **Manifest\-Designer**.  
  
3.  Wählen Sie auf der Registerkarte **Objekte** die Schaltfläche **Neu** aus.  
  
     Das Dialogfeld **Neue Anlage hinzufügen** wird geöffnet.  
  
4.  In der **Typ** aus, wählen Sie den Typ der Erweiterung hinzufügen.  
  
5.  Um eine Erweiterung oder des Inhalts Element hinzuzufügen, die in der aktuellen Projektmappe \(z. B. eine Elementvorlage oder eine kompilierte Assembly\) enthalten ist, führen Sie die folgenden Schritte aus:  
  
    1.  Wählen Sie in der Liste **Quelle** die Option **Ein Projekt in der aktuellen Projektmappe** aus.  
  
    2.  In der **Projekt** aus, wählen Sie den Namen der Erweiterung.  
  
    3.  In der **Einbetten in diesen Ordner** Geben Sie den Namen eines Ordners zum Einbetten der Ressource, und wählen Sie dann die **OK** Schaltfläche.  
  
6.  Zum Hinzufügen einer Erweiterung oder ein Inhaltselement, das in der aktuellen Projektmappe enthalten ist, führen Sie die folgenden Schritte aus:  
  
    1.  In der **Quelle** und wählen Sie im Listenfeld **Datei im Dateisystem**.  
  
    2.  In der **Pfad** Feld, geben Sie den vollständigen Pfad der Erweiterung kompilierte oder komprimierte Datei, oder verwenden Sie die **Durchsuchen** Schaltfläche, um die Datei zu suchen.  
  
    3.  In der **Einbetten in diesen Ordner** Geben Sie den Namen eines Ordners zum Einbetten der Ressource, und wählen Sie dann die **OK** Schaltfläche.  
  
7.  Wenn Sie Ihrem Paket, um zusätzliche Erweiterungen einschließen möchten, fügen Sie diese auf die gleiche Weise.  
  
8.  Erstellen Sie die Projektmappe.  
  
     [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] erstellt eine VSIX\-Datei enthält eine VSIX\-manifest\-Datei, eine \[Content\_Types\] .xml\-Datei und alle Anlagen Erweiterung, die Sie dem Projekt hinzugefügt.  
  
## Siehe auch  
 [VSIX\-Erweiterung Schemareferenz 2.0](../extensibility/vsix-extension-schema-2-0-reference.md)   
 [Suchen und Verwenden von Visual Studio\-Erweiterungen](../ide/finding-and-using-visual-studio-extensions.md)