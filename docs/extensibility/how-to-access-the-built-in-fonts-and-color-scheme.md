---
title: "Gewusst wie: Zugriff auf die integrierten Schriftarten und Farbschemas | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Schriftarten, die Zugriff auf integrierte"
  - "Schriftart und Farbe-Steuerelement [Visual Studio SDK] Kategorien"
  - "Farben, die Zugriff auf integrierte Schemas"
ms.assetid: 6905845e-e88e-4805-adcf-21da39108ec7
caps.latest.revision: 23
caps.handback.revision: 23
ms.author: "gregvanl"
manager: "ghogen"
---
# Gewusst wie: Zugriff auf die integrierten Schriftarten und Farbschemas
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die integrierte Entwicklungsumgebung \(IDE\) von Visual Studio verfügt über ein Schema von Schriftarten und Farben, das Editor\-Fenster zugeordnet ist. Sie erreichen dieses Schema über die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> Schnittstelle.  
  
 Um die integrierte Schriftarten und Farbschema zu verwenden, müssen ein VSPackage:  
  
-   Definieren Sie eine Kategorie für den Standarddienst für Schriftarten und Farben.  
  
-   Registrieren Sie die Kategorie mit dem Standardserver für Schriftarten und Farben.  
  
-   Der IDE empfehlen Sie, dass ein bestimmtes Fenster mithilfe der integrierten Elementen und Kategorien verwendet die `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer` und `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer` Schnittstellen.  
  
 Die IDE verwendet die resultierende Kategorie als Handle für das Fenster. Name der Kategorie wird angezeigt, der **Einstellungen anzeigen für:** Dropdown\-Feld in der **Schriftarten und Farben** Eigenschaftenseite.  
  
### Definieren Sie eine Kategorie mit integrierten Schriftarten und Farben  
  
1.  Erstellen Sie eine beliebige GUID.  
  
     Diese GUID dient zur eindeutigen Identifizierung eine Kategorie**.** Diese Kategorie verwendet die IDE Standard\-Schriftarten und Farben\-Spezifikation.  
  
    > [!NOTE]
    >  Beim Abrufen von Daten von Schriftart und Farbe mit der <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents> oder anderen Schnittstellen VSPackages mit dieser GUID um integrierte Informationen zu verweisen.  
  
2.  Eine Tabelle innerhalb des VSPackage Ressourcendatei \(.rc\), muss dem Kategorienamen hinzugefügt werden, damit sie lokalisiert werden kann, wenn Sie in der IDE angezeigt.  
  
     Weitere Informationen finden Sie unter [Adding or Deleting a String](/visual-cpp/windows/adding-or-deleting-a-string).  
  
### Registrieren Sie eine Kategorie mit integrierten Schriftarten und Farben  
  
1.  Erstellen Sie eine besondere Art von Kategorie Registrierungseintrag an folgendem Speicherort:  
  
     \[HKLM\\SOFTWARE\\Microsoft \\Visual Studio\\*\< Visual Studio\-Version \>*\\FontAndColors\\*\< Category \>*\]  
  
     *\< Category \>* der nicht lokalisierte Name der Kategorie.  
  
2.  Füllen Sie die Registrierung, um die vordefinierten Schriftarten und Farbschemas mit vier Werten verwenden:  
  
    |Name|Typ|Daten|Beschreibung|  
    |----------|---------|-----------|------------------|  
    |Kategorie|REG\_SZ|GUID|Ein beliebiger GUID, die eine Kategorie identifiziert, die die vordefinierten Schriftarten und Farbschemas enthält.|  
    |Package|REG\_SZ|GUID|{F5E7E71D\-1401\-11D1\-883B\-0000F87579D2}<br /><br /> Diese GUID wird von VSPackages sämtlicher verwendet, mit denen die Standardkonfigurationen der Schriftart und Farbe.|  
    |NameID|REG\_DWORD|ID|Die Ressourcen\-ID einen lokalisierbaren Kategorienamen in den VSPackage.|  
    |ToolWindowPackage|REG\_SZ|GUID|Die GUID für die VSPackage implementieren die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> Schnittstelle.|  
  
3.  
  
### So initiieren Sie die Verwendung der vom System bereitgestellten Schriftarten und Farben  
  
1.  Erstellen Sie eine Instanz der `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer` \-Schnittstelle als Teil der Implementierung und die Initialisierung des Fensters.  
  
2.  Rufen Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer.GetPropertyCategory%2A> \-Methode zum Abrufen einer Instanz der `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer` Schnittstelle entsprechend dem aktuellen <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> Instanz.  
  
3.  Rufen Sie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A> zweimal.  
  
    -   Rufen Sie einmal mit `VSEDITPROPID_ViewGeneral_ColorCategory`als Argument.  
  
    -   Rufen Sie einmal mit `VSEDITPROPID_ViewGeneral_FontCategory` als Argument.  
  
     Dies legt fest, und macht die Standarddienste für Schriftarten und Farben als Eigenschaft des Fensters.  
  
## Beispiel  
 Im folgende Beispiel wird die Verwendung der integrierten Schriftarten und Farben initiiert.  
  
```  
CComVariant vt;  
CComQIPtr<IVsTextEditorPropertyCategoryContainer> spPropCatContainer(m_spView);  
if (spPropCatContainer != NULL){  
    CComPtr<IVsTextEditorPropertyContainer> spPropContainer;  
    if (SUCCEEDED(spPropCatContainer->GetPropertyCategory(GUID_EditPropCategory_View_MasterSettings,   
                                                          &spPropContainer))){  
        CComVariant vt;CComVariant VariantGUID(bstrGuidText);  
        spPropContainer->SetProperty(VSEDITPROPID_ViewGeneral_FontCategory, VariantGUID);  
        spPropContainer->SetProperty(VSEDITPROPID_ViewGeneral_ColorCategory, VariantGUID);  
    }  
}  
```  
  
## Siehe auch  
 [Verwenden von Schriftarten und Farben](../extensibility/using-fonts-and-colors.md)   
 [Schriftart und Farbe Informationen für die farbliche Kennzeichnung Text abrufen](../extensibility/getting-font-and-color-information-for-text-colorization.md)   
 [Zugriff auf gespeicherte Schriftart\- und Farbschema](../extensibility/accessing-stored-font-and-color-settings.md)   
 [Schriftart und Farbe \(Übersicht\)](../extensibility/font-and-color-overview.md)