---
title: VSIX-Projektvorlage | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deploy packages
- publish extension
ms.assetid: b6c82167-e2a5-4cff-8c8b-2d72e2a9092c
caps.latest.revision: "21"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 24a2937b37aa339f85e197f6ff2bb49cbb0ce86f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="vsix-project-template"></a>VSIX-Projektvorlage
Sie können die VSIX-Projektvorlage verwenden, um eine oder mehrere Visual Studio-Erweiterungen in einem VSIX-Projekt zu umschließen, und veröffentlichen Sie das Paket auf die [Visual Studio Gallery](http://go.microsoft.com/fwlink/?LinkID=123847) Website.  
  
 VSIX-Bereitstellung unterstützt VSPackages, Assemblys, MEF-Komponenten, Projektvorlagen, Elementvorlagen, Toolbox-Steuerelementen und benutzerdefinierte Erweiterungstypen enthalten.  
  
> [!NOTE]
>  Um die VSIX-Projekten verwenden zu können, müssen Sie das Visual Studio SDK installieren. Weitere Informationen zu Visual Studio SDK, finden Sie unter [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="where-to-find-the-vsix-project-template"></a>Wo Sie die VSIX-Projektvorlage finden  
 Die VSIX-Projektvorlage finden Sie in der **neues Projekt** (Dialogfeld). Erweitern Sie entweder die **Visual Basic** Knoten oder die **Visual C#-** Knoten, und wählen Sie dann **Erweiterbarkeit**.  
  
> [!TIP]
>  Sie sollten sicherstellen, dass diese .NET Framework 4.5 oder höher angegeben ist, in der Dropdownliste am oberen Rand der **neues Projekt** (Dialogfeld).  
  
## <a name="uses-of-the-vsix-project-template"></a>Verwendet die VSIX-Projektvorlage  
 Die VSIX-Projektvorlage weist zwei Hauptanwendungsgebiete:  
  
-   Zum Bereitstellen von Projektvorlagen, Elementvorlagen und anderen Erweiterungen, die noch nicht VSIX-Unterstützung verfügen.  
  
-   Um die Ausgaben der mehrere Erweiterungen in einem Bereitstellungspaket zu umschließen.  
  
 Sie müssen nicht die VSIX-Projektvorlage verwenden zum Bereitstellen von VSPackages oder andere Arten von Erweiterungen, auf denen bereits VSIX unterstützen.  
  
## <a name="packaging-an-extension-in-an-empty-vsix-project"></a>Verpacken einer Erweiterung in ein leeres VSIX-Projekt  
 Sie können eine vorhandene Erweiterung oder eine Erweiterung, die nicht bereits VSIX unterstützen, indem Sie ihn in ein leeres VSIX-Projekt einzuschließen, verpacken. Die Erweiterung zu umschließende muss ein Typ, der vom unterstützt wird die [VSIX-Schema](../extensibility/vsix-extension-schema-2-0-reference.md).  
  
#### <a name="to-package-an-extension-by-using-a-vsix-project"></a>So verpacken Sie eine Erweiterung mithilfe eines VSIX-Projekts  
  
1.  Erstellen Sie die Projekte, aus denen die Erweiterung besteht.  
  
2.  Erstellen Sie ein VSIX-Projekt mithilfe der **VSIX-Projekt** Vorlage.  
  
     Datei "Source.Extension.vsixmanifest" wird geöffnet, **Manifest-Designer**.  
  
3.  Auf der **Bestand** Registerkarte, und wählen Sie die **neu** Schaltfläche.  
  
     Die **neue Anlage hinzufügen** Dialogfeld wird angezeigt.  
  
4.  In der **Typ** wählen Sie den Typ der hinzuzufügenden Erweiterung.  
  
5.  Um eine Erweiterung oder des Inhalts Element hinzuzufügen, die in der aktuellen Projektmappe (z. B. eine Elementvorlage oder eine kompilierte Assembly) enthalten ist, führen Sie die folgenden Schritte aus:  
  
    1.  In der **Quelle** wählen **ein Projekt in der aktuellen Projektmappe**.  
  
    2.  In der **Projekt** wählen Sie den Namen der Erweiterung.  
  
    3.  In der **Einbetten in diesen Ordner** Geben Sie den Namen eines Ordners, in dem das Medienobjekt einzubetten, und wählen Sie dann die **OK** Schaltfläche.  
  
6.  Zum Hinzufügen einer Erweiterung oder ein Inhaltselement, das in der aktuellen Projektmappe enthalten ist, führen Sie die folgenden Schritte aus:  
  
    1.  In der **Quelle** , und wählen Sie im Listenfeld **Datei im Dateisystem**.  
  
    2.  In der **Pfad** Feld, geben Sie den vollständigen Pfad zu den kompilierten oder komprimierten Erweiterungsdatei oder verwenden Sie die **Durchsuchen** Schaltfläche, um die Datei zu suchen.  
  
    3.  In der **Einbetten in diesen Ordner** Geben Sie den Namen eines Ordners, in dem das Medienobjekt einzubetten, und wählen Sie dann die **OK** Schaltfläche.  
  
7.  Wenn Sie Ihrem Paket, um zusätzliche Erweiterungen enthalten soll, müssen fügen Sie ihn hinzu, auf die gleiche Weise.  
  
8.  Erstellen Sie die Projektmappe.  
  
     [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]erstellt eine VSIX-Datei, die mit einer VSIX-manifest-Datei, eine [Content_Types] .xml-Datei und alle Erweiterungs-Objekte, die Sie dem Projekt hinzugefügt.  
  
## <a name="see-also"></a>Siehe auch  
 [VSIX-Erweiterung Schemareferenz 2.0](../extensibility/vsix-extension-schema-2-0-reference.md)   
 [Suchen und Verwenden von Visual Studio-Erweiterungen](../ide/finding-and-using-visual-studio-extensions.md)