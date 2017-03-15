---
title: 'Gewusst wie: Angeben eines Anwendungssymbols (Visual Basic, C#) | Microsoft-Dokumentation'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- icons [Visual Studio], application
- application properties [Visual Studio], icons
- application icons [Visual Studio]
ms.assetid: ad8e14ed-adc2-45b6-a0be-818b16d5616f
caps.latest.revision: 18
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 6889879efe06e8b0541aa08017292a92a736ea50

---
# <a name="how-to-specify-an-application-icon-visual-basic-c"></a>Gewusst wie: Angeben eines Anwendungssymbols (Visual Basic, C#))
Die `Icon`-Eigenschaft für ein Projekt gibt die Symboldatei (.ico) an, die für die kompilierte Anwendung im Datei-Explorer und in der Windows-Taskleiste angezeigt wird.  
  
 Auf die `Icon`-Eigenschaft können Sie im **Projekt-Designer** über den Bereich **Anwendung** zugreifen. Dort finden Sie eine Liste der Symbole, die dem Projekt entweder als Ressourcen oder als Inhaltsdateien hinzugefügt wurden.  
  
> [!NOTE]
>  Wenn Sie die Symboleigenschaft für eine Anwendung festgelegt haben, können Sie auch die `Icon`-Eigenschaft für jedes **Fenster** oder **Formular** in der Anwendung festlegen. Informationen zu Fenstersymbolen für eigenständige WPF-Anwendungen (Windows Presentation Foundation) finden Sie unter <xref:System.Windows.Window.Icon%2A>-Eigenschaft.  
  
### <a name="to-specify-an-application-icon"></a>So legen Sie ein Anwendungssymbol fest  
  
1.  Wählen Sie im **Projektmappen-Explorer** einen Projektknoten (nicht den Knoten **Projektmappe**) aus.  
  
2.  Wählen Sie in der Menüleiste **Projekt** und **Eigenschaften** aus.  
  
3.  Wählen Sie, wenn der **Projekt-Designer** angezeigt wird, die Registerkarte **Anwendung** aus.  
  
4.  **(Visual Basic)** Wählen Sie in der Liste **Symbol** eine Symboldatei (.ico) aus.  
  
     **C#** Wählen Sie in der Nähe der Liste **Symbol** die Schaltfläche **\<Durchsuchen...>** aus, und navigieren Sie zum Speicherort der gewünschten Symboldatei.  
  
## <a name="see-also"></a>Siehe auch  
 [Application Page, Project Designer (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)   
 [Seite „Anwendung“, Projekt-Designer (C#)](../ide/reference/application-page-project-designer-csharp.md)   
 [Verwalten von Anwendungseigenschaften](../ide/application-properties.md)  
 [Gewusst wie: Hinzufügen oder Entfernen von Ressourcen](http://msdn.microsoft.com/en-us/7b77bc06-3952-4799-b029-def3f8f7f88d)


<!--HONumber=Feb17_HO4-->


