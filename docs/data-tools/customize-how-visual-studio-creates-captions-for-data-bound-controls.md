---
title: "Gewusst wie: Anpassen der Erstellung von Beschriftungen f&#252;r datengebundene Steuerelemente durch Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "Beschriftungen, Datengebunden"
  - "Datenquellenfenster, Bezeichnungsbeschriftungen"
  - "Bezeichnungsbeschriftungen, Datenquellenfenster"
  - "Smart-Beschriftungen"
ms.assetid: 6d4d15f8-4d78-42fd-af64-779ae98d62c8
caps.latest.revision: 12
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Gewusst wie: Anpassen der Erstellung von Beschriftungen f&#252;r datengebundene Steuerelemente durch Visual Studio
Es muss eine Besonderheit beachtet werden, wenn Sie Elemente aus dem [Datenquellenfenster](../Topic/Data%20Sources%20Window.md) auf den Windows Forms\-Designer ziehen: Die Spaltennamen in den Beschriftungstiteln werden in eine lesbarere Zeichenfolge umformatiert, wenn mindestens zwei miteinander verkettete Wörter gefunden werden.  Sie können die Erstellung dieser Beschriftungen anpassen, indem Sie die Werte **SmartCaptionExpression**, **SmartCaptionReplacement** und **SmartCaptionSuffix** im Registrierungsschlüssel **HKEY\_CURRENT\_USER\\Software\\Microsoft\\VisualStudio\\10.0\\Daten\-Designer** festlegen.  
  
> [!NOTE]
>  Dieser Registrierungsschlüssel ist nicht vorhanden, bevor Sie ihn erstellen.  
  
 Die intelligente Beschriftungserstellung wird durch den regulären Ausdruck gesteuert, der als Wert von **SmartCaptionExpression** angegeben ist.  Durch Hinzufügen des Registrierungsschlüssels **Daten\-Designer** wird der reguläre Standardausdruck überschrieben, durch den Beschriftungstitel gesteuert werden.  Weitere Informationen zu regulären Ausdrücken finden Sie unter [Verwenden von regulären Ausdrücken in Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).  
  
 In der folgenden Tabelle werden die Registrierungswerte beschrieben, durch die die Beschriftungstitel gesteuert werden.  
  
|Registrierungselement|Beschreibung|  
|---------------------------|------------------|  
|SmartCaptionExpression|Der reguläre Ausdruck, der für den Mustervergleich verwendet wird.|  
|SmartCaptionReplacement|Das Format, in dem die Gruppen angezeigt werden, die durch den Mustervergleich mit **SmartCaptionExpression** ermittelt wurden.|  
|SmartCaptionSuffix|Eine optionale Zeichenfolge, die an das Ende der Beschriftung angefügt wird.|  
  
 In den folgenden Tabellen sind die internen Standardeinstellungen für diese Registrierungswerte aufgeführt.  
  
|Element|Standardwert|Erklärung|  
|-------------|------------------|---------------|  
|**SmartCaptionExpression**|\(\\\\p{Ll}\)\(\\\\p{Lu}\)&#124;\_\+|Liefert eine Übereinstimmung, wenn auf einen Kleinbuchstaben ein Großbuchstabe oder ein Unterstrich folgt.|  
|**SmartCaptionReplacement**|$1 $2|$1 stellt die Zeichen dar, die dem Ausdruck in der ersten Klammer entsprechen, und $2 stellt die Zeichen dar, die dem Ausdruck in der zweiten Klammer entsprechen.  Für die Ersetzung wird die erste Übereinstimmung, ein Leerzeichen und dann die zweite Übereinstimmung verwendet.|  
|**SmartCaptionSuffix**|:|Stellt ein Zeichen dar, das an die zurückgegebene Zeichenfolge angefügt wird.  Wenn die Beschriftung z. B. `Company Name` lautet, wird sie durch das Suffix zu `Company Name:`.|  
  
> [!CAUTION]
>  Beim Arbeiten im Registrierungs\-Editor ist große Sorgfalt geboten.  Erstellen Sie eine Sicherungskopie der Registrierung, bevor Sie sie bearbeiten.  Die unsachgemäße Verwendung des Registrierungs\-Editors kann ernste Probleme verursachen und u. U. eine Neuinstallation des Betriebssystems erforderlich machen.  Microsoft kann nicht gewährleisten, dass durch unsachgemäße Verwendung des Registrierungs\-Editors entstandene Probleme wieder behoben werden können.  Die Verwendung des Registrierungs\-Editors erfolgt auf eigenes Risiko.  
>   
>  Der folgende KnowledgeBase\-Artikel enthält Anweisungen für das Sichern, Bearbeiten und Wiederherstellen der Registrierung: [Informationen zur Windows\-Registrierung für erfahrene Benutzer](http://support.microsoft.com/default.aspx?scid=kb;en-us;256986) \(http:\/\/support.microsoft.com\/default.aspx?scid\=kb;en\-us;256986\)  
  
### So ändern Sie das Verhalten der intelligenten Beschriftungserstellung vom Datenquellenfenster aus  
  
1.  Öffnen Sie ein Befehlsfenster, indem Sie im **Startmenü** auf **Ausführen** klicken.  
  
2.  Geben Sie im Dialogfeld **Ausführen** den Ausdruck `regedit` ein, und klicken Sie auf **OK**.  
  
3.  Erweitern Sie den Knoten **HKEY\_CURRENT\_USER**.  
  
4.  Erweitern Sie den Knoten **Software**.  
  
5.  Erweitern Sie den Knoten **Microsoft**.  
  
6.  Erweitern Sie den Knoten **VisualStudio**.  
  
7.  Klicken Sie mit der rechten Maustaste auf den Knoten **10.0**, und erstellen Sie einen neuen **Schlüssel** mit dem Namen `Daten-Designer`.  
  
8.  Klicken Sie mit der rechten Maustaste auf den Knoten **Daten\-Designer**, und erstellen Sie eine neue **Zeichenfolge** mit dem Namen `SmartCaptionExpression`.  
  
9. Klicken Sie mit der rechten Maustaste auf den Knoten **Daten\-Designer**, und erstellen Sie eine neue **Zeichenfolge** mit dem Namen `SmartCaptionReplacement`.  
  
10. Klicken Sie mit der rechten Maustaste auf den Knoten **Daten\-Designer**, und erstellen Sie eine neue **Zeichenfolge** mit dem Namen `SmartCaptionSuffix`.  
  
11. Klicken Sie mit der rechten Maustaste auf das Element **SmartCaptionExpression**, und wählen Sie **Ändern** aus.  
  
12. Geben Sie den regulären Ausdruck ein, der vom **Datenquellenfenster** verwendet werden soll.  
  
13. Klicken Sie mit der rechten Maustaste auf das Element **SmartCaptionReplacement**, und wählen Sie **Ändern** aus.  
  
14. Geben Sie in der Ersetzungszeichenfolge das neue Format für die mit dem regulären Ausdruck übereinstimmenden Muster an.  
  
15. Klicken Sie mit der rechten Maustaste auf das Element **SmartCaptionSuffix**, und wählen Sie **Ändern** aus.  
  
16. Geben Sie die Zeichen ein, die am Ende der Beschriftung angezeigt werden sollen.  
  
     Wenn Sie das nächste Mal Elemente aus dem **Datenquellenfenster** ziehen, werden die Beschriftungstitel gemäß den gewählten Registrierungswerten erstellt.  
  
### So schalten Sie die intelligente Beschriftungserstellung aus  
  
1.  Öffnen Sie ein Befehlsfenster, indem Sie im **Startmenü** auf **Ausführen** klicken.  
  
2.  Geben Sie im Dialogfeld **Ausführen** den Ausdruck `regedit` ein, und klicken Sie auf **OK**.  
  
3.  Erweitern Sie den Knoten **HKEY\_CURRENT\_USER**.  
  
4.  Erweitern Sie den Knoten **Software**.  
  
5.  Erweitern Sie den Knoten **Microsoft**.  
  
6.  Erweitern Sie den Knoten **VisualStudio**.  
  
7.  Klicken Sie mit der rechten Maustaste auf den Knoten **10.0**, und erstellen Sie einen neuen **Schlüssel** mit dem Namen `Daten-Designer`.  
  
8.  Klicken Sie mit der rechten Maustaste auf den Knoten **Daten\-Designer**, und erstellen Sie eine neue **Zeichenfolge** mit dem Namen `SmartCaptionExpression`.  
  
9. Klicken Sie mit der rechten Maustaste auf den Knoten **Daten\-Designer**, und erstellen Sie eine neue **Zeichenfolge** mit dem Namen `SmartCaptionReplacement`.  
  
10. Klicken Sie mit der rechten Maustaste auf den Knoten **Daten\-Designer**, und erstellen Sie eine neue **Zeichenfolge** mit dem Namen `SmartCaptionSuffix`.  
  
11. Klicken Sie mit der rechten Maustaste auf das Element **SmartCaptionExpression**, und wählen Sie **Ändern** aus.  
  
12. Geben Sie `(.*)` als Wert ein.  Dadurch wird die gesamte Zeichenfolge als Übereinstimmung ermittelt.  
  
13. Klicken Sie mit der rechten Maustaste auf das Element **SmartCaptionReplacement**, und wählen Sie **Ändern** aus.  
  
14. Geben Sie `$1` als Wert ein.  Die Zeichenfolge wird dann durch den übereinstimmenden Wert ersetzt. Da aber die gesamte Zeichenfolge als Übereinstimmung ermittelt wurde, bleibt sie unverändert.  
  
     Wenn Sie das nächste Mal Elemente aus dem **Datenquellenfenster** ziehen, werden die Beschriftungstitel mit unveränderter Beschriftung erstellt.  
  
## Siehe auch  
 [Reguläre Ausdrücke von .NET Framework](../Topic/.NET%20Framework%20Regular%20Expressions.md)   
 [Binden von Windows Forms\-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Vorbereiten der Anwendung auf den Empfang von Daten](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Abrufen von Daten für die Anwendung](../data-tools/fetching-data-into-your-application.md)   
 [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Bearbeiten von Daten in der Anwendung](../data-tools/editing-data-in-your-application.md)   
 [Überprüfen von Daten](../Topic/Validating%20Data.md)   
 [Speichern von Daten](../data-tools/saving-data.md)