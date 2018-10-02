---
title: Toolbox, Registerkarte „HTML“ | Microsoft-Dokumentation
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
- vs.toolbox.html
helpviewer_keywords:
- Toolbox, HTML tab
- HTML Designer, setting options
- HTML tab in Toolbox
ms.assetid: 9bfdd3b8-f5ac-4a5f-bdbf-c2b4e97641d8
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 52180c730e6d7a03da549595ab658339f1a2d44c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47524139"
---
# <a name="toolbox-html-tab"></a>Toolbox, Registerkarte „HTML“
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Toolbox, Registerkarte "HTML"](https://docs.microsoft.com/visualstudio/ide/reference/toolbox-html-tab).  
  
  
Die Registerkarte **HTML** der Toolbox stellt Komponenten bereit, die für Webseiten und Webformulare nützlich sind. Öffnen Sie zuerst ein Dokument zur Bearbeitung im HTML-Designer, um diese Registerkarte anzuzeigen. Klicken Sie im Menü **Ansicht** auf **Toolbox** und dann auf die Registerkarte **HTML**.  
  
 Erstellen Sie eine Instanz eines Tools auf der Registerkarte **HTML**, indem Sie entweder auf das Tool doppelklicken und es zu ihrem Dokument an der aktuellen Einfügemarke hinzufügen oder das Tool auswählen und es an die gewünschte Position auf der Bearbeitungsoberfläche ziehen.  
  
## <a name="tasks"></a>Aufgaben  
  
-   [How to: Manage the Toolbox Window (Vorgehensweise: Verwalten des Toolbox-Fensters)](http://msdn.microsoft.com/en-us/a022c3fe-298c-4a59-a48f-b050da90ebc2)  
  
-   [Vorgehensweise: Ändern von Registerkarten der Toolbox](http://msdn.microsoft.com/en-us/21285050-cadd-455a-b1f5-a2289a89c4db)  
  
## <a name="ui-elements"></a>Benutzeroberflächenelemente  
 Die folgenden Tools sind standardmäßig auf der Registerkarte „HTML“ verfügbar.  
  
 **Pointer**  
 ![ASP.NET Mobile-Designer, HTML-Seite, Zeiger](../../ide/reference/media/vxpointer.gif "vxPointer")  
  
 Dieses Tool ist standardmäßig ausgewählt, wenn eine Toolboxregisterkarte geöffnet wird. Es kann nicht gelöscht werden. Mithilfe des Zeigers können Sie Objekte auf die Entwurfsoberfläche ziehen, die Größe der Objekte ändern und sie auf der Seite oder dem Formular neu anordnen. Weitere Informationen finden Sie unter [How to: Manage the Toolbox Window (Vorgehensweise: Verwalten des Toolbox-Fensters)](http://msdn.microsoft.com/en-us/a022c3fe-298c-4a59-a48f-b050da90ebc2) und [Vorgehensweise: Ändern von Registerkarten der Toolbox](http://msdn.microsoft.com/en-us/21285050-cadd-455a-b1f5-a2289a89c4db).  
  
 **Input (Button)**  
 ![Schaltfläche auf HTML-Webseite](../../ide/reference/media/vxbutton.gif "vxButton")  
  
 Fügt ein `input`-Element vom Typ `type="button"` ein. Bearbeiten Sie die `name`-Eigenschaft, um den angezeigten Text zu ändern. In der Standardeinstellung wird `id="Button1"` für die erste Schaltfläche eingefügt, `id="Button2"` für die zweite usw.  
  
 Wenn Sie **Input (Button)** auf die Entwurfsoberfläche ziehen, wird ein HTML-Markup ähnlich dem folgenden in das Dokument eingefügt:  
  
```  
<input id="Button1" type="button" value="Button" name="Button1">  
```  
  
 Weitere Informationen finden Sie unter [HTML-Input-Steuerelemente](http://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [Deklarationssyntax des HtmlInputButton-Serversteuerelements](http://msdn.microsoft.com/en-us/99ccf7fb-7e2a-4ba1-bcd9-981b619a16aa), [NIB: Vorgehensweise: Erstellen von Skripts und Bearbeiten von Ereignishandlern](http://msdn.microsoft.com/en-us/69d71d13-c68b-4ecd-869b-a42edf6d1f6d), [ Schaltfläche "-Webserversteuerelemente Inhaltszuordnung](http://msdn.microsoft.com/library/66b3ce28-3b93-4f0a-951f-42fb5bb5fddf), <xref:System.Web.UI.HtmlControls.HtmlInputButton>, <xref:System.Web.UI.HtmlControls.HtmlButton>, und <xref:System.Web.UI.WebControls.Button>.  
  
 **Input (Reset)**  
 ![HTMLpageResetButton-Bildschirmabbildung](../../ide/reference/media/vxreset.gif "vxReset")  
  
 Fügt ein `input`-Element vom Typ `type="reset"` ein. Bearbeiten Sie die `name`-Eigenschaft, um den angezeigten Text zu ändern. In der Standardeinstellung wird `id="Reset1"` für die erste Reset-Schaltfläche eingefügt, `id="Reset2"` für die zweite usw.  
  
 Wenn Sie **Input (Reset)** auf die Entwurfsoberfläche ziehen, wird ein HTML-Markup ähnlich dem folgenden in das Dokument eingefügt:  
  
```  
<input id="Reset1" type="reset" value="Reset" name="Reset1">  
```  
  
 Weitere Informationen finden Sie unter [HTML-Input-Steuerelemente](http://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [Deklarationssyntax des HtmlInputReset-Serversteuerelements](http://msdn.microsoft.com/en-us/cfc1f1fb-d33a-464d-9bb5-204e66174979), <xref:System.Web.UI.HtmlControls.HtmlInputButton>, und <xref:System.Web.UI.WebControls.Button>.  
  
 **Input (Submit)**  
 ![HTMLpageToolbarSubmitButton-Bildschirmabbildung](../../ide/reference/media/vxsubmit.gif "vxSubmit")  
  
 Fügt ein `input`-Element vom Typ `type="submit"` ein. Bearbeiten Sie die `name`-Eigenschaft, um den angezeigten Text zu ändern. In der Standardeinstellung wird `id="Submit1"` für die erste Submit-Schaltfläche eingefügt, `id="Submit2"` für die zweite usw.  
  
 Wenn Sie **Input (Submit)** auf die Entwurfsoberfläche ziehen, wird ein HTML-Markup ähnlich dem folgenden in das Dokument eingefügt:  
  
```  
<input id="Submit1" type="submit" value="Submit" name="Submit1">  
```  
  
 Weitere Informationen finden Sie unter [HTML-Input-Steuerelemente](http://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [Deklarationssyntax des HtmlInputSubmit-Serversteuerelements](http://msdn.microsoft.com/en-us/eef2a157-f184-4ce9-b256-d1eacc7930f2), <xref:System.Web.UI.HtmlControls.HtmlInputButton>, und <xref:System.Web.UI.WebControls.Button>.  
  
 **Input (Text)**  
 ![HTMLpageToolbarTextField-Bildschirmabbildung](../../ide/reference/media/vxtextfield.gif "vxTextfield")  
  
 Fügt ein `input`-Element vom Typ `type="text"` in das Dokument ein. Bearbeiten Sie das `value`-Attribut, um den angezeigten Standardtext zu ändern. In der Standardeinstellung wird `id="Text1"` für das erste Textfeld eingefügt, `id="Text2"` für das zweite usw.  
  
 Wenn Sie **Input (Text)** auf die Entwurfsoberfläche ziehen, wird ein HTML-Markup ähnlich dem folgenden in das Dokument eingefügt:  
  
```  
<input id="Text1" TYPE="text" value="Text Field" name="Text1">  
```  
  
 Weitere Informationen finden Sie unter [HTML-Input-Steuerelemente](http://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [Deklarationssyntax des HtmlInputText-Serversteuerelements](http://msdn.microsoft.com/en-us/87060d90-a11c-434d-9fc9-b03a8487041e), [Übersicht über das TextBox-Steuerelement](http://msdn.microsoft.com/library/ab354bc1-f23a-48fc-93d8-d4d7c1b7396f), <xref:System.Web.UI.HtmlControls.HtmlInputText>, und <xref:System.Web.UI.WebControls.TextBox>.  
  
> [!IMPORTANT]
>  Es wird empfohlen, alle Benutzereingaben zu validieren. Weitere Informationen finden Sie unter [Überprüfen der Benutzereingabe in ASP.NET-Webseiten](http://msdn.microsoft.com/library/4ad3dacb-89e0-4cee-89ac-40a3f2a85461).  
  
 **Input (File)**  
 ![HTML-Seite, Dateifeld](../../ide/reference/media/vxfilefield.gif "vxFilefield")  
  
 Fügt ein `input`-Element vom Typ `type="file"` in das Dokument ein. In der Standardeinstellung wird `id="File1"` für das erste Dateifeld eingefügt, `id="File2"` für das zweite usw.  
  
 Wenn Sie **Input (File)** auf die Entwurfsoberfläche ziehen, wird ein HTML-Markup ähnlich dem folgenden in das Dokument eingefügt:  
  
```  
<input id="File1" type="file" name="File1">  
```  
  
 Weitere Informationen finden Sie unter [HTML-Input-Steuerelemente](http://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [Deklarationssyntax des HtmlInputFile-Serversteuerelements](http://msdn.microsoft.com/en-us/a817b4a0-056f-4c17-a696-b9fdcde43db6), und <xref:System.Web.UI.HtmlControls.HtmlInputFile>.  
  
> [!IMPORTANT]
>  Es wird empfohlen, alle Benutzereingaben zu validieren. Weitere Informationen finden Sie unter [Überprüfen der Benutzereingabe in ASP.NET-Webseiten](http://msdn.microsoft.com/library/4ad3dacb-89e0-4cee-89ac-40a3f2a85461).  
  
 **Input (Password)**  
 ![Visual Studio, Password Field](../../ide/reference/media/vxpassword.gif "vxPassword")  
  
 Fügt ein `input`-Element vom Typ `type="password"` ein. In der Standardeinstellung wird `id="Password1"` für das erste Kennwortfeld eingefügt, `id="Password2"` für das zweite usw.  
  
 Wenn Sie **Input (Password)** auf die Entwurfsoberfläche ziehen, wird ein HTML-Markup ähnlich dem folgenden in das Dokument eingefügt:  
  
```  
<input id="Password1" type="password" name="Password1">  
```  
  
 Weitere Informationen finden Sie unter [Input-Steuerelemente (HTML)](http://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [Deklarative Syntax des HtmlInputPassword-Serversteuerelements](http://msdn.microsoft.com/en-us/df703dd0-1624-4e5a-a547-c97f2f331b9f), [Vorgehensweise: Einrichten eines TextBox-Webserversteuerelements für die Kennworteingabe](http://msdn.microsoft.com/library/5b5069f3-64a1-435a-aee6-da263f4e6310) und [Exemplarische Vorgehensweise: Validieren der Benutzereingabe in einer Web Forms-Seite](http://msdn.microsoft.com/library/7141d6ba-34f3-410b-b5cd-2102a24cb436).  
  
> [!IMPORTANT]
>  Wenn Ihre Anwendung Benutzernamen und Kennwörter überträgt, sollten Sie Ihre Webseite so konfigurieren, dass sie Secure Sockets Layer (SSL) verwendet, um die Übertragung zu verschlüsseln. Weitere Informationen finden Sie unter „Securing Connections with SSL“ („Sichern von Verbindungen mit SSL“) im [IIS Operations Guide (IIS-Benutzerhandbuch)](http://go.microsoft.com/fwlink/?linkid=47856). Es wird außerdem empfohlen, alle Benutzereingaben zu validieren. Weitere Informationen finden Sie unter [Überprüfen der Benutzereingabe in ASP.NET-Webseiten](http://msdn.microsoft.com/library/4ad3dacb-89e0-4cee-89ac-40a3f2a85461).  
  
 **Input (Check box)**  
 ![HTML-Webseiten-Toolbox, Kontrollkästchenoption](../../ide/reference/media/vxcheckbox.gif "vxCheckbox")  
  
 Fügt ein `input`-Element vom Typ `type="checkbox"` ein. Bearbeiten Sie die `name`-Eigenschaft, um den angezeigten Text zu ändern. In der Standardeinstellung wird `id="Checkbox1"` für das erste Kontrollkästchen eingefügt, `id="Checkbox2"` für das zweite usw.  
  
 Wenn Sie **Input (Check box)** auf die Entwurfsoberfläche ziehen, wird ein HTML-Markup ähnlich dem folgenden in das Dokument eingefügt:  
  
```  
<input id="Checkbox1" type="checkbox" name="Checkbox1">   
```  
  
 Weitere Informationen finden Sie unter [HTML-Input-Steuerelemente](http://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [Deklarationssyntax des HtmlInputCheckBox-Serversteuerelements](http://msdn.microsoft.com/en-us/4a509586-89d8-4ccf-a0b8-b9160ce6e4a6), [aktiviert und "CheckBoxList" Webserver-Steuerelemente: Übersicht](http://msdn.microsoft.com/library/3028dfd3-e2c5-451d-9150-d02c8ffb92bf), <xref:System.Web.UI.HtmlControls.HtmlInputCheckBox>, und <xref:System.Web.UI.WebControls.CheckBox>.  
  
 **Input (Radio)**  
 ![VisualStudioHTMLpageRadioButton-Bildschirmabbildung](../../ide/reference/media/vxradio.gif "vxRadio")  
  
 Fügt ein `input`-Element vom Typ `type="radio"` ein. Bearbeiten Sie die `name`-Eigenschaft, um den angezeigten Text zu ändern. In der Standardeinstellung wird `id="Radio1"` für das erste Optionsfeld eingefügt, `id="Radio2"` für das zweite usw.  
  
 Wenn Sie **Input (Radio)** auf die Entwurfsoberfläche ziehen, wird ein HTML-Markup ähnlich dem folgenden in das Dokument eingefügt:  
  
```  
<input id="Radio1" type="radio" name="Radio1">  
```  
  
 Weitere Informationen finden Sie unter [HTML-Input-Steuerelemente](http://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [Deklarationssyntax des HtmlInputRadioButton-Serversteuerelements](http://msdn.microsoft.com/en-us/6e60ff63-cc57-46ef-bf96-e829e204ba33), [RadioButton- und RadioButtonList Webserver-Steuerelemente: Übersicht](http://msdn.microsoft.com/library/20eb383c-4b59-432b-bba3-e9d785107747), <xref:System.Web.UI.HtmlControls.HtmlInputRadioButton>, und <xref:System.Web.UI.WebControls.RadioButton>.  
  
 **Input (Hidden)**  
 ![HTML-Seite, Hidden-Element](../../ide/reference/media/vxhidden.gif "vxhidden")  
  
 Fügt ein `input`-Element vom Typ `type="hidden"` ein. In der Standardeinstellung wird `id="Hidden1"` für das erste ausgeblendete Feld eingefügt, `id="Hidden2"` für das zweite usw.  
  
 Wenn Sie **Input (Hidden)** auf die Entwurfsoberfläche ziehen, wird ein HTML-Markup ähnlich dem folgenden in das Dokument eingefügt:  
  
```  
<input id="Hidden1" type="hidden" name="Hidden1">   
```  
  
 Weitere Informationen finden Sie unter [HTML-Input-Steuerelemente](http://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [Deklarationssyntax des HtmlInputHidden-Serversteuerelements](http://msdn.microsoft.com/en-us/4194e44d-1d74-4bfc-9cc7-743a2e1ea5f9), und <xref:System.Web.UI.HtmlControls.HtmlInputHidden>.  
  
 **Textarea**  
 ![HTML-Seiten-Toolbox, Text Area](../../ide/reference/media/vxtextarea.gif "vxTextarea")  
  
 Fügt ein `textarea`-Element ein. Sie können die Größe des Textbereichs ändern oder die Bildlaufleisten verwenden, um Text außerhalb des Anzeigebereichs anzuzeigen. Bearbeiten Sie das `value`-Attribut, um den angezeigten Standardtext zu ändern. In der Standardeinstellung wird `id="textarea1"` für den ersten Textbereich eingefügt, `id=" textarea 2"` für den zweiten usw.  
  
 Wenn Sie **Textarea** auf die Entwurfsoberfläche ziehen, wird ein HTML-Markup ähnlich dem folgenden in das Dokument eingefügt:  
  
```  
<textarea id=" textarea 1 name=" textarea 1" rows=2 cols=20></textarea>   
```  
  
 Weitere Informationen finden Sie unter [Deklarationssyntax des HtmlTextArea-Serversteuerelements](http://msdn.microsoft.com/en-us/5a103ffa-235b-4452-ba2b-a4fb8ba8cb87), <xref:System.Web.UI.HtmlControls.HtmlTextArea>, und <xref:System.Web.UI.WebControls.TextBox>.  
  
> [!IMPORTANT]
>  Es wird empfohlen, alle Benutzereingaben zu validieren. Weitere Informationen finden Sie unter [Überprüfen der Benutzereingabe in ASP.NET-Webseiten](http://msdn.microsoft.com/library/4ad3dacb-89e0-4cee-89ac-40a3f2a85461).  
  
 **Table**  
 ![HTMLpageToolbarTable-Bildschirmabbildung](../../ide/reference/media/vxtable.gif "vxTable")  
  
 Fügt ein `table`-Element ein.  
  
 Wenn Sie **Table** auf die Entwurfsoberfläche ziehen, wird ein HTML-Markup ähnlich dem folgenden in das Dokument eingefügt:  
  
```  
<table cellspacing="1" width="75%" border=1> <tr><td></td></tr></table>   
```  
  
 Weitere Informationen finden Sie unter [Deklarationssyntax des HtmlTable-Serversteuerelements](http://msdn.microsoft.com/en-us/625b06d8-0f69-4112-a1d4-8ef2a9fbcda9), [Table-, TableRow- und TableCell Web Server Control Overview](http://msdn.microsoft.com/library/2fbd0582-cf69-4c8d-9e35-21f35e2cee1a), <xref:System.Web.UI.HtmlControls.HtmlTable>, und <xref:System.Web.UI.WebControls.Table>.  
  
 **Image**  
 ![HTML-Seite, Image-Element](../../ide/reference/media/vximage.gif "vxImage")  
  
 Fügt ein `img`-Element ein. Bearbeiten Sie dieses Element, und geben Sie dessen `src` und `alt`-Text an.  
  
 Wenn Sie **Image** auf die Entwurfsoberfläche ziehen, wird ein HTML-Markup ähnlich dem folgenden in das Dokument eingefügt:  
  
```  
<img alt="" src="">  
```  
  
 Weitere Informationen finden Sie unter [Deklarationssyntax des HtmlImage-Serversteuerelements](http://msdn.microsoft.com/en-us/528430e8-ced1-47d1-8db2-942e734a61f6), [Übersicht über das Image-Steuerelement](http://msdn.microsoft.com/library/096a8d8d-58ee-4ee8-ab82-6594a0f3a0a9), <xref:System.Web.UI.HtmlControls.HtmlImage>, <xref:System.Web.UI.HtmlControls.HtmlInputImage>, und <xref:System.Web.UI.WebControls.Image>.  
  
 **Auswählen**  
 ![HTML-Seiten-Toolbox, Dropdownfeld](../../ide/reference/media/vxdropdown.gif "vxDropdown")  
  
 Fügt ein Dropdown-`select`-Element ein (ohne `size`-Attribut). In der Standardeinstellung wird `id="select1"` für das erste Listenfeld eingefügt, `id="select2"` für das zweite usw.  
  
 Wenn Sie **Select** auf die Entwurfsoberfläche ziehen, wird ein HTML-Markup ähnlich dem folgenden in das Dokument eingefügt:  
  
```  
<select id="select1" name="select1"><option selected></option></select>  
```  
  
 Sie können ein mehrzeiliges `select`-Element erstellen, indem Sie den Wert der size-Eigenschaft erhöhen.  
  
 Weitere Informationen finden Sie unter [Deklarationssyntax des HtmlSelect-Serversteuerelements](http://msdn.microsoft.com/en-us/ee93bdec-b343-441a-a8ff-56ffcafe9ae5), [NIB: Vorgehensweise: Erstellen von Skripts und Bearbeiten von Ereignishandlern](http://msdn.microsoft.com/en-us/69d71d13-c68b-4ecd-869b-a42edf6d1f6d), [DropDownList-Steuerelement Übersicht über Webserver](http://msdn.microsoft.com/library/517dd1a4-8df3-4c9f-8c89-1549a1aee608), [Übersicht über das ListBox-Webserversteuerelement](http://msdn.microsoft.com/library/c08ee025-787a-408d-858e-a4a5fdb61d97), <xref:System.Web.UI.HtmlControls.HtmlSelect>, und <xref:System.Web.UI.WebControls.DropDownList>.  
  
 **Horizontal Rule**  
 ![HTML-Seite, Horizontal Rule-Element](../../ide/reference/media/vxhorizontal.gif "vxHorizontal")  
  
 Fügt ein `hr`-Element ein. Um die Stärke der Linie zu erhöhen, bearbeiten Sie das `size`-Attribut.  
  
 Wenn Sie **Horizontal Rule** auf die Entwurfsoberfläche ziehen, wird ein HTML-Markup ähnlich dem folgenden in das Dokument eingefügt:  
  
```  
<hr width="100%" size=1>   
```  
  
 Weitere Informationen finden Sie unter [Horizontal Rule-Steuerelement (HTML)](http://msdn.microsoft.com/library/bf6df0a8-9844-404d-8a9a-3455b0180f2f).  
  
 **Div**  
 ![HTML-Seite, Label](../../ide/reference/media/vxlabel.gif "vxLabel")  
  
 Fügt ein `div`-Element ein, das ein `ms_positioning="FlowLayout"`-Attribut enthält. Mit Ausnahme der Breite und Höhe ist dieses Element mit einem Flow Layout Panel identisch. Fügen Sie dem Starttag ein `class="stylename"`-Attribut hinzu, um den Text zu formatieren, der im `div`-Element enthalten ist.  
  
 Wenn Sie **Div** auf die Entwurfsoberfläche ziehen, wird ein HTML-Markup ähnlich dem folgenden in das Dokument eingefügt:  
  
```  
<div ms_positioning="FlowLayout" style="width: 70px; position: relative; height: 15px">Label</div>  
```  
  
 Weitere Informationen finden Sie unter [HTML-Div-Steuerelement](http://msdn.microsoft.com/library/585fa702-4408-4af1-a92b-68d77ee5e995), [Übersicht über das Label-Steuerelement](http://msdn.microsoft.com/library/990558d1-4b22-4f28-b100-78a434b3c5ac), und <xref:System.Web.UI.WebControls.Label>.  
  
## <a name="see-also"></a>Siehe auch  
 [Toolbox](../../ide/reference/toolbox.md)   
 [Registerkarte „Standard“, Toolbox](http://msdn.microsoft.com/library/35e9320d-fcbd-474b-8b8f-55705e9a1870)   
 [HTML-Steuerelemente](http://msdn.microsoft.com/library/83bc6f7e-a2b5-4fe9-9a34-eb34aef673be)



