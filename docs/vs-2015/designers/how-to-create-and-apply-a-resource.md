---
title: Erstellen und Anwenden einer Ressource | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.XamlDesigner.CreateResource
- VS.XamlDesigner.EditResource
ms.assetid: 3ff4006d-659d-4073-9a41-06ff85e6cfdf
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 75041cb9db00b48ea81dfe9a8639c41e4267262c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47523700"
---
# <a name="how-to-create-and-apply-a-resource"></a>So erstellen Sie eine Ressource und wenden Sie an
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [erstellen und Anwenden einer Ressource](https://docs.microsoft.com/visualstudio/designers/how-to-create-and-apply-a-resource).  
  
Stile und Vorlagen für Elemente im XAML-Designer werden in wieder verwendbaren Einheiten namens Ressourcen gespeichert. Stile ermöglichen es Ihnen, Elementeigenschaften festzulegen und diese Einstellungen für ein konsistentes Erscheinungsbild für mehrere Elemente wiederzuverwenden. Eine [ControlTemplate](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.controltemplate.aspx) definiert die Darstellung eines Steuerelements und kann auch als Ressource angewendet werden. Weitere Informationen finden Sie unter [Schnellstart: Formatieren von Steuerelementen](http://go.microsoft.com/fwlink/?LinkID=248239) und [Schnellstart: Steuerelementvorlagen](http://go.microsoft.com/fwlink/?LinkID=247982).  
  
 Wenn Sie eine neue Ressource von einer vorhandenen Eigenschaft, [Formatvorlage](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.style.aspx) oder `ControlTemplate` erstellen, können Sie im Dialogfeld **Ressource erstellen** die Ressource auf Anwendungs-, Dokument- oder Elementebene definieren. Diese Ebenen bestimmen, wo Sie die Ressource verwenden können. Wenn Sie beispielsweise die Ressource auf der Elementebene definieren, kann die Ressource nur auf das Element angewendet werden, für das sie erstellt wurde. Sie können die Ressource auch in einem Ressourcenverzeichnis speichern. Hierbei handelt es sich um eine eigene Datei, die in anderen Projekten wieder verwendet werden kann.  
  
### <a name="to-create-a-new-resource"></a>So erstellen Sie eine neue Ressource  
  
1.  Erstellen Sie mit einer im XAML-Designer geöffneten XAML-Datei ein Element, oder wählen Sie ein Element im Fenster "Dokumentgliederung" aus.  
  
2.  Wählen Sie im Eigenschaftenfenster den Eigenschaftenmarker aus, der als Feldsymbol rechts neben einem Eigenschaftswert angezeigt wird, und wählen Sie dann **In neue Ressource konvertieren** aus. Ein weißes Feldsymbol gibt einen Standardwert an, und ein schwarzes Feldsymbol gibt in der Regel an, dass eine lokale Ressource angewendet wurde.  
  
     Das Dialogfeld für das Erstellen einer Ressource wird angezeigt. Dieses Dialogfeld wird angezeigt, wenn Sie eine Ressource mit einem Pinsel erstellen:  
  
     ![Dialogfeld „Ressource erstellen“](../designers/media/xaml-create-resource.png "xaml_create_resource")  
  
3.  Geben Sie im Feld **Name (Schlüssel)** einen Schlüsselnamen ein. Dies ist der Name, den Sie verwenden können, wenn Sie möchten, dass andere Elemente auf die Ressource verweisen.  
  
4.  Wählen Sie unter **Definieren in** die Option aus, die angibt, wo die Ressource definiert werden soll:  
  
    -   Damit die Ressource für alle Dokumente in der Anwendung verfügbar ist, wählen Sie **Anwendung** aus.  
  
    -   Damit die Ressource nur für das aktuelle Dokument zur Verfügung steht, wählen Sie **Dieses Dokument** aus.  
  
    -   Um die Ressource nur für das Element zur Verfügung zu stellen, aus dem die Ressource oder die dazugehörigen untergeordneten Elemente erstellt wurden, wählen Sie **Dieses Dokument** und anschließend in der Dropdownliste *Element*: *Name* aus.  
  
    -   Um die Ressource in einer Ressourcenverzeichnisdatei zu definieren, die in anderen Projekten wiederverwendet werden kann, klicken Sie auf **Ressourcenverzeichnis**, und wählen Sie dann eine vorhandene Ressourcenverzeichnisdatei, z.B. **StandardStyles.xaml**, in der Dropdownliste aus.  
  
5.  Klicken Sie auf **OK**, um die Ressource zu erstellen und auf das Element anzuwenden, aus dem Sie sie erstellt haben.  
  
### <a name="to-apply-a-resource-to-an-element-or-property"></a>So wenden Sie eine Ressource auf ein Element oder auf eine Eigenschaft an  
  
1.  Wählen Sie im Fenster "Dokumentgliederung" das Element aus, auf das eine Ressource angewendet werden soll.  
  
2.  Führen Sie einen der folgenden Schritte aus:  
  
    -   Anwenden einer Ressource auf eine Eigenschaft Wählen Sie im Eigenschaftenfenster den Eigenschaftenmarker neben dem Eigenschaftswert und dann **Lokale Ressource** oder **Systemressource** aus. Anschließend wählen Sie eine verfügbare Ressource aus der angezeigten Liste aus.  
  
         Wenn eine Ressource, die Sie erwarten, nicht angezeigt wird, kann dies möglicherweise daran liegen, dass der Typ der Ressource nicht mit dem Typ der Eigenschaft übereinstimmt.  
  
    -   Anwenden eines Stils oder einer Steuerelementvorlagenressource auf ein Steuerelement Öffnen Sie das Kontextmenü für ein Steuerelement im Fenster „Dokumentgliederung“, wählen Sie **Vorlage bearbeiten** oder **Zusätzliche Vorlagen bearbeiten** und dann **Ressource anwenden** aus. Wählen Sie anschließend den Namen der Steuerelementvorlage aus der angezeigten Liste aus.  
  
        > [!NOTE]
        >  **Vorlage bearbeiten** wird verwendet, um Steuerelementvorlagen anzuwenden. **Zusätzliche Vorlage bearbeiten** wird verwendet, um andere Vorlagentypen anzuwenden.  
  
     Ressourcen können immer dann angewendet werden, wenn sie kompatibel sind. So kann eine Pinselressource beispielsweise auf die **Foreground**-Eigenschaft eines <xref:Windows.UI.Xaml.Controls.TextBox>-Steuerelements angewendet werden.  
  
### <a name="to-edit-a-resource"></a>So bearbeiten Sie eine Ressource  
  
1.  Wählen Sie ein Element auf der Zeichenfläche oder im Fenster "Dokumentgliederung" aus.  
  
2.  Wählen Sie den Eigenschaftenmarker „Standard“ oder „Lokal“ rechts neben der Eigenschaft im Eigenschaftenfenster aus, und wählen Sie dann **Ressource bearbeiten** zum Öffnen des Dialogfelds **Ressource bearbeiten** aus.  
  
3.  Ändern Sie die Optionen für die Ressource.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen einer Benutzeroberfläche mit dem XAML-Designer](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md)



