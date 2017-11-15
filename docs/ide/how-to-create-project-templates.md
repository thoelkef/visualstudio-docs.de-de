---
title: 'Vorgehensweise: Erstellen von Projektvorlagen | Microsoft-Dokumentation'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.ExportTemplateWizard
helpviewer_keywords:
- Visual Studio templates, creating project templates
- project templates, metadata files
- Visual Studio templates, project templates
- project templates, custom template locations
- project templates, creating
ms.assetid: a1a6999d-a34c-48a8-b1cf-027eb5c76398
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a473ac2be65acc9b08455fe687b52468f5ca9fa6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-create-project-templates"></a>Gewusst wie: Erstellen von Projektvorlagen
Diese Vorgehensweise ermöglicht Ihnen das Erstellen einer Vorlage mithilfe des **Assistenten zum Exportieren von Vorlagen**, bei dem Ihre Vorlage in einer ZIP-Datei verpackt wird. Sie können für eine verbesserte Bereitstellung auch Vorlagen im Dateiformat VSIX erstellen, indem Sie die Erweiterung des „Assistenten zum Exportieren von Vorlagen“ oder Vorlagen verwenden, die in [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] enthalten sind. Außerdem können Sie Vorlagen manuell erstellen.  
  
### <a name="to-create-a-custom-project-template-with-the-standard-export-template-wizard"></a>So erstellen Sie eine benutzerdefinierte Projektvorlage mit dem Standard-Assistenten zum Exportieren von Vorlagen  
  
1.  Erstellen eines Projekts.  
  
    > [!NOTE]
    >  Verwenden Sie nur gültige Bezeichnerzeichen beim Benennen eines Projekts, das als Quelle für eine Vorlage verwendet wird. Eine aus einem Projekt exportierte Vorlage, das mit ungültigen Zeichen benannt wurde, kann in zukünftigen Projekten, die auf dieser Vorlage basieren, Kompilierungsfehler verursachen. Weitere Informationen zu gültigen Bezeichnerzeichen finden Sie unter [Declared Element Names (Namen deklarierter Elemente)](/dotnet/visual-basic/programming-guide/language-features/declared-elements/declared-element-names).  
  
2.  Bearbeiten Sie das Projekt solange, bis es als Vorlage exportiert werden kann.  
  
3.  Ändern Sie gegebenenfalls die Codedateien, um anzugeben, an welcher Stelle Parameterersetzungen stattfinden sollen. Weitere Informationen zu Parameterersetzungen finden Sie unter [Vorgehensweise: Ersetzen von Parametern in einer Vorlage](../ide/how-to-substitute-parameters-in-a-template.md).  
  
4.  Klicken Sie im Menü **Projekt** auf **Vorlage exportieren**. Der **Assistent zum Exportieren von Vorlagen** wird geöffnet.  
  
5.  Klicken Sie auf **Projektvorlage**.  
  
6.  Wenn sich in Ihrer aktuellen Projektmappe mehr als ein Projekt befindet, müssen Sie das Projekt auswählen, das Sie als Vorlage exportieren möchten.  
  
7.  Klicken Sie auf **Weiter**.  
  
8.  Wählen Sie ein Symbol und ein Vorschaubild für die Vorlage aus. Diese werden im Dialogfeld **Neues Projekt** angezeigt.  
  
9. Geben Sie einen Namen und eine Beschreibung für die Vorlage ein.  
  
10. Klicken Sie auf **Fertig stellen**. Das Projekt wird als ZIP-Datei exportiert und am angegebenen Speicherort platziert. Außerdem wird es in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] importiert, wenn diese Option ausgewählt wurde.  
  
     Wenn [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] installiert ist, können Sie die fertige Vorlage für die Bereitstellung in einer VSIX-Datei umschließen, indem Sie die Vorlage **VSIX-Projekt** verwenden. Weitere Informationen finden Sie unter [Erste Schritte mit der VSIX-Projektvorlage](../extensibility/getting-started-with-the-vsix-project-template.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen von Projekt- und Elementvorlagen](../ide/creating-project-and-item-templates.md)   
 [Gewusst wie: Erstellen von Elementvorlagen](../ide/how-to-create-item-templates.md)
