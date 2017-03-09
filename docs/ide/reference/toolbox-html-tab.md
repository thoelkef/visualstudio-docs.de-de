---
title: "Toolbox, Registerkarte &quot;HTML&quot; | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.toolbox.html"
helpviewer_keywords: 
  - "HTML-Designer, Festlegen von Optionen"
  - "HTML (Registerkarte in der Toolbox)"
  - "Toolbox, HTML (Registerkarte)"
ms.assetid: 9bfdd3b8-f5ac-4a5f-bdbf-c2b4e97641d8
caps.latest.revision: 13
caps.handback.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Toolbox, Registerkarte &quot;HTML&quot;
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Die Registerkarte **HTML** der Toolbox enthält Komponenten, die auf Webseiten und Web Forms verwendet werden können.  Öffnen Sie zum Anzeigen dieser Registerkarte zuerst im HTML\-Designer ein Dokument für die Bearbeitung.  Klicken Sie im Menü **Ansicht** auf **Toolbox** und anschließend auf die Registerkarte **HTML** der Toolbox.  
  
 Doppelklicken Sie zum Erstellen einer Instanz eines Tools auf der Registerkarte **HTML** entweder auf das Tool, um es an der aktuellen Einfügemarke im Dokument einzufügen, oder wählen Sie das Tool aus, und ziehen Sie es in der Bearbeitungsoberfläche an die gewünschte Position.  
  
## Aufgaben  
  
-   [How to: Manage the Toolbox Window](http://msdn.microsoft.com/de-de/a022c3fe-298c-4a59-a48f-b050da90ebc2)  
  
-   [How to: Manipulate Toolbox Tabs](http://msdn.microsoft.com/de-de/21285050-cadd-455a-b1f5-a2289a89c4db)  
  
## Benutzeroberflächenelemente  
 In der Standardeinstellung stehen auf der Registerkarte HTML die folgenden Tools zur Verfügung.  
  
 **Zeiger**  
 Dieses Tool ist standardmäßig bei jedem Öffnen einer Toolbox\-Registerkarte ausgewählt.  Es kann nicht gelöscht werden.  Mithilfe des Zeigers können Sie Objekte auf die Oberfläche in der Entwurfsansicht ziehen, die Größe der Objekte ändern und sie auf der Seite oder dem Formular neu anordnen.  Weitere Informationen finden Sie unter [How to: Manage the Toolbox Window](http://msdn.microsoft.com/de-de/a022c3fe-298c-4a59-a48f-b050da90ebc2) und [How to: Manipulate Toolbox Tabs](http://msdn.microsoft.com/de-de/21285050-cadd-455a-b1f5-a2289a89c4db).  
  
 **Input \(Button\)**  
 Fügt ein `input`\-Element vom Typ `type="button"` ein.  Bearbeiten Sie zum Ändern des angezeigten Texts die `name`\-Eigenschaft.  In der Standardeinstellung wird `id="Button1"` für das erste button\-Element eingefügt, `id="Button2"` für das zweite usw.  
  
 Wenn Sie **Input \(Button\)** auf die Bearbeitungsfläche der Entwurfsansicht ziehen, wird HTML\-Markup ähnlich dem folgenden in das Dokument eingefügt:  
  
```  
<input id="Button1" type="button" value="Button" name="Button1">  
```  
  
 Weitere Informationen finden Sie unter [HTML Input Controls](../Topic/HTML%20Input%20Controls.md), [Deklarative Syntax des HtmlInputButton\-Serversteuerelements](http://msdn.microsoft.com/de-de/99ccf7fb-7e2a-4ba1-bcd9-981b619a16aa), [NIB: How to: Create Scripts and Edit Event Handlers](http://msdn.microsoft.com/de-de/69d71d13-c68b-4ecd-869b-a42edf6d1f6d), [Button Web Server Controls Content Map](../Topic/Button%20Web%20Server%20Controls%20Content%20Map.md), <xref:System.Web.UI.HtmlControls.HtmlInputButton>, <xref:System.Web.UI.HtmlControls.HtmlButton> und <xref:System.Web.UI.WebControls.Button>.  
  
 **Input \(Reset\)**  
 Fügt ein `input`\-Element vom Typ `type="reset"` ein.  Bearbeiten Sie zum Ändern des angezeigten Texts die `name`\-Eigenschaft.  In der Standardeinstellung wird `id="Reset1"` für die erste Schaltfläche zum Zurücksetzen eingefügt, `id="Reset2"` für die zweite usw.  
  
 Wenn Sie **Input \(Reset\)** auf die Bearbeitungsfläche der Entwurfsansicht ziehen, wird HTML\-Markup ähnlich dem folgenden in das Dokument eingefügt:  
  
```  
<input id="Reset1" type="reset" value="Reset" name="Reset1">  
```  
  
 Weitere Informationen finden Sie unter [HTML Input Controls](../Topic/HTML%20Input%20Controls.md), [Deklarative Syntax des HtmlInputReset\-Serversteuerelements](http://msdn.microsoft.com/de-de/cfc1f1fb-d33a-464d-9bb5-204e66174979), <xref:System.Web.UI.HtmlControls.HtmlInputButton> und <xref:System.Web.UI.WebControls.Button>.  
  
 **Input \(Submit\)**  
 Fügt ein `input`\-Element vom Typ `type="submit"` ein.  Bearbeiten Sie zum Ändern des angezeigten Texts die `name`\-Eigenschaft.  In der Standardeinstellung wird `id="Submit1"` für das erste submit button\-Element eingefügt, `id="Submit2"` für das zweite usw.  
  
 Wenn Sie **Input \(Submit\)** auf die Bearbeitungsfläche der Entwurfsansicht ziehen, wird HTML\-Markup ähnlich dem folgenden in das Dokument eingefügt:  
  
```  
<input id="Submit1" type="submit" value="Submit" name="Submit1">  
```  
  
 Weitere Informationen finden Sie unter [HTML Input Controls](../Topic/HTML%20Input%20Controls.md), [Deklarative Syntax des HtmlInputSubmit\-Serversteuerelements](http://msdn.microsoft.com/de-de/eef2a157-f184-4ce9-b256-d1eacc7930f2), <xref:System.Web.UI.HtmlControls.HtmlInputButton> und <xref:System.Web.UI.WebControls.Button>.  
  
 **Input \(Text\)**  
 Fügt ein `input`\-Element vom Typ `type="text"` in das Dokument ein.  Bearbeiten Sie zum Ändern des angezeigten Standardtexts das `value`\-Attribut.  In der Standardeinstellung wird `id="Text1"` für das erste text field\-Element eingefügt, `id="Text2"` für das zweite usw.  
  
 Wenn Sie **Input \(Text\)** auf die Bearbeitungsfläche der Entwurfsansicht ziehen, wird HTML\-Markup ähnlich dem folgenden in das Dokument eingefügt:  
  
```  
<input id="Text1" TYPE="text" value="Text Field" name="Text1">  
```  
  
 Weitere Informationen finden Sie unter [HTML Input Controls](../Topic/HTML%20Input%20Controls.md), [Deklarative Syntax des HtmlInputText\-Serversteuerelements](http://msdn.microsoft.com/de-de/87060d90-a11c-434d-9fc9-b03a8487041e), [TextBox Web Server Control Overview](../Topic/TextBox%20Web%20Server%20Control%20Overview.md), <xref:System.Web.UI.HtmlControls.HtmlInputText> und <xref:System.Web.UI.WebControls.TextBox>.  
  
> [!IMPORTANT]
>  Es wird empfohlen, dass Sie alle Benutzereingaben überprüfen.  Weitere Informationen finden Sie unter [Validating User Input in ASP.NET Web Pages](../Topic/Validating%20User%20Input%20in%20ASP.NET%20Web%20Pages.md).  
  
 **Input \(File\)**  
 Fügt ein `input`\-Element vom Typ `type="file"` in das Dokument ein.  In der Standardeinstellung wird `id="File1"` für das erste file field\-Element eingefügt, `id="File2"` für das zweite usw.  
  
 Wenn Sie **Input \(File\)** auf die Bearbeitungsfläche der Entwurfsansicht ziehen, wird HTML\-Markup ähnlich dem folgenden in das Dokument eingefügt:  
  
```  
<input id="File1" type="file" name="File1">  
```  
  
 Weitere Informationen finden Sie unter [HTML Input Controls](../Topic/HTML%20Input%20Controls.md), [Deklarative Syntax des HtmlInputFile\-Serversteuerelements](http://msdn.microsoft.com/de-de/a817b4a0-056f-4c17-a696-b9fdcde43db6) und <xref:System.Web.UI.HtmlControls.HtmlInputFile>.  
  
> [!IMPORTANT]
>  Es wird empfohlen, dass Sie alle Benutzereingaben überprüfen.  Weitere Informationen finden Sie unter [Validating User Input in ASP.NET Web Pages](../Topic/Validating%20User%20Input%20in%20ASP.NET%20Web%20Pages.md).  
  
 **Input \(Password\)**  
 Fügt ein `input`\-Element vom Typ `type="password"` ein.  In der Standardeinstellung wird `id="Password1"` für das erste password field\-Element eingefügt, `id="Password2"` für das zweite usw.  
  
 Wenn Sie **Input \(Password\)** auf die Bearbeitungsfläche der Entwurfsansicht ziehen, wird HTML\-Markup ähnlich dem folgenden in das Dokument eingefügt:  
  
```  
<input id="Password1" type="password" name="Password1">  
```  
  
 Weitere Informationen finden Sie unter [HTML Input Controls](../Topic/HTML%20Input%20Controls.md), [Deklarative Syntax des HtmlInputPassword\-Serversteuerelements](http://msdn.microsoft.com/de-de/df703dd0-1624-4e5a-a547-c97f2f331b9f), [How to: Set a TextBox Web Server Control for Password Entry](../Topic/How%20to:%20Set%20a%20TextBox%20Web%20Server%20Control%20for%20Password%20Entry.md) und [Walkthrough: Validating User Input in a Web Forms Page](../Topic/Walkthrough:%20Validating%20User%20Input%20in%20a%20Web%20Forms%20Page.md).  
  
> [!IMPORTANT]
>  Wenn über die Anwendung Benutzernamen und Kennwörter übertragen werden, sollten Sie die Website so konfigurieren, dass die übertragenen Daten mit Secure Sockets Layer \(SSL\) verschlüsselt werden.  Weitere Informationen finden Sie unter "Securing Connections with SSL" im [IIS Operations Guide](http://go.microsoft.com/fwlink/?linkid=47856).  Darüber hinaus wird empfohlen, dass Sie alle Benutzereingaben überprüfen.  Weitere Informationen finden Sie unter [Validating User Input in ASP.NET Web Pages](../Topic/Validating%20User%20Input%20in%20ASP.NET%20Web%20Pages.md).  
  
 **Input \(Check box\)**  
 Fügt ein `input`\-Element vom Typ `type="checkbox"` ein.  Bearbeiten Sie zum Ändern des angezeigten Texts die `name`\-Eigenschaft.  In der Standardeinstellung wird `id="Checkbox1"` für das erste check box\-Element eingefügt, `id="Checkbox2"` für das zweite usw.  
  
 Wenn Sie **Input \(Check box\)** auf die Bearbeitungsfläche der Entwurfsansicht ziehen, wird HTML\-Markup ähnlich dem folgenden in das Dokument eingefügt:  
  
```  
<input id="Checkbox1" type="checkbox" name="Checkbox1">   
```  
  
 Weitere Informationen finden Sie unter [HTML Input Controls](../Topic/HTML%20Input%20Controls.md), [Deklarative Syntax des HtmlInputCheckBox\-Serversteuerelements](http://msdn.microsoft.com/de-de/4a509586-89d8-4ccf-a0b8-b9160ce6e4a6), [CheckBox and CheckBoxList Web Server Controls Overview](../Topic/CheckBox%20and%20CheckBoxList%20Web%20Server%20Controls%20Overview.md), <xref:System.Web.UI.HtmlControls.HtmlInputCheckBox> und <xref:System.Web.UI.WebControls.CheckBox>.  
  
 **Input \(Radio\)**  
 Fügt ein `input`\-Element vom Typ `type="radio"` ein.  Bearbeiten Sie zum Ändern des angezeigten Texts die `name`\-Eigenschaft.  In der Standardeinstellung wird `id="Radio1"` für das erste radio button\-Element eingefügt, `id="Radio2"` für das zweite usw.  
  
 Wenn Sie **Input \(Radio\)** auf die Bearbeitungsfläche der Entwurfsansicht ziehen, wird HTML\-Markup ähnlich dem folgenden in das Dokument eingefügt:  
  
```  
<input id="Radio1" type="radio" name="Radio1">  
```  
  
 Weitere Informationen finden Sie unter [HTML Input Controls](../Topic/HTML%20Input%20Controls.md), [Deklarative Syntax des HtmlInputRadioButton\-Serversteuerelements](http://msdn.microsoft.com/de-de/6e60ff63-cc57-46ef-bf96-e829e204ba33), [RadioButton and RadioButtonList Web Server Controls Overview](../Topic/RadioButton%20and%20RadioButtonList%20Web%20Server%20Controls%20Overview.md), <xref:System.Web.UI.HtmlControls.HtmlInputRadioButton> und <xref:System.Web.UI.WebControls.RadioButton>.  
  
 **Input \(Hidden\)**  
 Fügt ein `input`\-Element vom Typ `type="hidden"` ein.  In der Standardeinstellung wird `id="Hidden1"` für das erste hidden field\-Element eingefügt, `id="Hidden2"` für das zweite usw.  
  
 Wenn Sie **Input \(Hidden\)** auf die Bearbeitungsfläche der Entwurfsansicht ziehen, wird HTML\-Markup ähnlich dem folgenden in das Dokument eingefügt:  
  
```  
<input id="Hidden1" type="hidden" name="Hidden1">   
```  
  
 Weitere Informationen finden Sie unter [HTML Input Controls](../Topic/HTML%20Input%20Controls.md), [Deklarative Syntax des HtmlInputHidden\-Serversteuerelements](http://msdn.microsoft.com/de-de/4194e44d-1d74-4bfc-9cc7-743a2e1ea5f9) und <xref:System.Web.UI.HtmlControls.HtmlInputHidden>.  
  
 **Textarea**  
 Fügt ein `textarea`\-Element ein.  Sie können die Größe des Textbereichs ändern oder mithilfe der entsprechenden Schiebeleisten den Text außerhalb des Anzeigebereichs anzeigen.  Bearbeiten Sie zum Ändern des angezeigten Standardtexts das `value`\-Attribut.  In der Standardeinstellung wird `id="textarea1"` für das erste text area\-Element eingefügt, `id=" textarea 2"` für das zweite usw.  
  
 Wenn Sie **Textarea** auf die Bearbeitungsfläche der Entwurfsansicht ziehen, wird HTML\-Markup ähnlich dem folgenden in das Dokument eingefügt:  
  
```  
<textarea id=" textarea 1 name=" textarea 1" rows=2 cols=20></textarea>   
```  
  
 Weitere Informationen finden Sie unter [Deklarative Syntax des HtmlTextArea\-Serversteuerelements](http://msdn.microsoft.com/de-de/5a103ffa-235b-4452-ba2b-a4fb8ba8cb87), <xref:System.Web.UI.HtmlControls.HtmlTextArea> und <xref:System.Web.UI.WebControls.TextBox>.  
  
> [!IMPORTANT]
>  Es wird empfohlen, dass Sie alle Benutzereingaben überprüfen.  Weitere Informationen finden Sie unter [Validating User Input in ASP.NET Web Pages](../Topic/Validating%20User%20Input%20in%20ASP.NET%20Web%20Pages.md).  
  
 **Tabelle**  
 Fügt ein `table`\-Element ein.  
  
 Wenn Sie **Table** auf die Bearbeitungsfläche der Entwurfsansicht ziehen, wird HTML\-Markup ähnlich dem folgenden in das Dokument eingefügt:  
  
```  
<table cellspacing="1" width="75%" border=1> <tr><td></td></tr></table>   
```  
  
 Weitere Informationen finden Sie unter [Deklarative Syntax des HtmlTable\-Serversteuerelements](http://msdn.microsoft.com/de-de/625b06d8-0f69-4112-a1d4-8ef2a9fbcda9), [Table, TableRow, and TableCell Web Server Control Overview](../Topic/Table,%20TableRow,%20and%20TableCell%20Web%20Server%20Control%20Overview.md), <xref:System.Web.UI.HtmlControls.HtmlTable> und <xref:System.Web.UI.WebControls.Table>.  
  
 **Bild**  
 Fügt ein `img`\-Element ein.  Bearbeiten Sie dieses Element, um seinen `src`\- und `alt`\-Text anzugeben.  
  
 Wenn Sie **Image** auf die Bearbeitungsfläche der Entwurfsansicht ziehen, wird HTML\-Markup ähnlich dem folgenden in das Dokument eingefügt:  
  
```  
<img alt="" src="">  
```  
  
 Weitere Informationen finden Sie unter [Deklarative Syntax des HtmlImage\-Serversteuerelements](http://msdn.microsoft.com/de-de/528430e8-ced1-47d1-8db2-942e734a61f6), [Image Web Server Control Overview](../Topic/Image%20Web%20Server%20Control%20Overview.md), <xref:System.Web.UI.HtmlControls.HtmlImage>, <xref:System.Web.UI.HtmlControls.HtmlInputImage> und <xref:System.Web.UI.WebControls.Image>.  
  
 **Select**  
 Fügt ein Dropdown\-`select`\-Element ein \(ohne `size`\-Attribut\).  In der Standardeinstellung wird `id="select1"` für das erste list box\-Element eingefügt, `id="select2"` für das zweite usw.  
  
 Wenn Sie **Select** auf die Bearbeitungsfläche der Entwurfsansicht ziehen, wird HTML\-Markup ähnlich dem folgenden in das Dokument eingefügt:  
  
```  
<select id="select1" name="select1"><option selected></option></select>  
```  
  
 Sie können ein mehrzeiliges `select`\-Element erstellen, indem Sie den Wert der Größeneigenschaft erhöhen.  
  
 Weitere Informationen finden Sie unter [Deklarative Syntax des HtmlSelect\-Serversteuerelements](http://msdn.microsoft.com/de-de/ee93bdec-b343-441a-a8ff-56ffcafe9ae5), [NIB: How to: Create Scripts and Edit Event Handlers](http://msdn.microsoft.com/de-de/69d71d13-c68b-4ecd-869b-a42edf6d1f6d), [DropDownList Web Server Control Overview](../Topic/DropDownList%20Web%20Server%20Control%20Overview.md), [ListBox Web Server Control Overview](../Topic/ListBox%20Web%20Server%20Control%20Overview.md), <xref:System.Web.UI.HtmlControls.HtmlSelect> und <xref:System.Web.UI.WebControls.DropDownList>.  
  
 **Horizontal Rule**  
 Fügt ein `hr`\-Element ein.  Bearbeiten Sie zum Vergrößern der Linienstärke das `size`\-Attribut.  
  
 Wenn Sie **Horizontal Rule** auf die Bearbeitungsfläche der Entwurfsansicht ziehen, wird HTML\-Markup ähnlich dem folgenden in das Dokument eingefügt:  
  
```  
<hr width="100%" size=1>   
```  
  
 Weitere Informationen finden Sie unter [HTML Horizontal Rule Control](../Topic/HTML%20Horizontal%20Rule%20Control.md).  
  
 **Div**  
 Fügt ein `div`\-Element ein, das ein `ms_positioning="FlowLayout"`\-Attribut umfasst.  Mit Ausnahme von width und height ist dieses Element mit einem Flow Layout Panel identisch.  Fügen Sie zum Formatieren des im `div`\-Element enthaltenen Texts dem Starttag ein `class="stylename"`\-Attribut hinzu.  
  
 Wenn Sie **Div** auf die Bearbeitungsfläche der Entwurfsansicht ziehen, wird HTML\-Markup ähnlich dem folgenden in das Dokument eingefügt:  
  
```  
<div ms_positioning="FlowLayout" style="width: 70px; position: relative; height: 15px">Label</div>  
```  
  
 Weitere Informationen finden Sie unter [HTML Div Control](../Topic/HTML%20Div%20Control.md), [Label Web Server Control Overview](../Topic/Label%20Web%20Server%20Control%20Overview.md) und <xref:System.Web.UI.WebControls.Label>.  
  
## Siehe auch  
 [Toolbox](../../ide/reference/toolbox.md)   
 [Registerkarte 'Standard', Werkzeugkasten](../Topic/Standard%20Tab,%20Toolbox.md)   
 [HTML Controls](../Topic/HTML%20Controls%20for%20ASP.NET%20Web%20Pages.md)