---
title: "Vorgehensweise: Zugriff auf die integrierten Schriftarten und Farbschemas für | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- fonts, accessing built-in
- font and color control [Visual Studio SDK], categories
- colors, accessing built-in schemes
ms.assetid: 6905845e-e88e-4805-adcf-21da39108ec7
caps.latest.revision: "23"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ae5c64d0272b998d27a9eb5753c04ae764c3af8f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-access-the-built-in-fonts-and-color-scheme"></a>Vorgehensweise: Zugriff auf die integrierten Schriftarten und Farbschemas
Die integrierte Entwicklungsumgebung (IDE) von Visual Studio verfügt über ein Schema von Schriftarten und Farben, das im Editor-Fenster zugeordnet ist. Sie erreichen dieses Schema über die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> Schnittstelle.  
  
 Um die integrierte Schriftarten und Farbschema zu verwenden, müssen eine VSPackage ein:  
  
-   Definieren Sie eine Kategorie für die Verwendung mit der Standarddienst für Schriftarten und Farben.  
  
-   Registrieren Sie die Kategorie mit den Standardserver für Schriftarten und Farben.  
  
-   Empfehlen der IDE, dass ein bestimmtes Fenster mithilfe der integrierten Anzeigeelementen und Kategorien verwendet die `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer` und `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer` Schnittstellen.  
  
 Die IDE verwendet die resultierende Kategorie als ein Handle für das Fenster. Name der Kategorie wird angezeigt, der **Einstellungen anzeigen für:** Dropdown-Feld in der **Schriftarten und Farben** Eigenschaftenseite.  
  
### <a name="to-define-a-category-using-built-in-fonts-and-colors"></a>Um eine Kategorie mit integrierten Schriftarten und Farben zu definieren.  
  
1.  Erstellen Sie eine beliebige GUID.  
  
     Diese GUID dient zur eindeutigen Identifizierung eine Kategorie**.** Diese Kategorie wird wiederverwendet, die IDE standardmäßig Schriftarten und Farben-Spezifikation.  
  
    > [!NOTE]
    >  Beim Abrufen von Schriftart und Farbe Daten mit der <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents> oder anderen Schnittstellen verwenden, VSPackages diesen GUID um integrierte Informationen verweisen.  
  
2.  Eine Zeichenfolgentabelle in die VSPackage Ressourcendatei (.rc), einer muss den Namen der Kategorie hinzugefügt werden, damit sie lokalisiert werden kann, wie erforderlich, wenn Sie in der IDE angezeigt.  
  
     Weitere Informationen finden Sie unter [hinzufügen oder Löschen von Zeichenfolgen](/cpp/windows/adding-or-deleting-a-string).  
  
### <a name="to-register-a-category-using-built-in-fonts-and-colors"></a>So registrieren eine Kategorie mit integrierten Schriftarten und Farben  
  
1.  Erstellen Sie eine besondere Art von Kategorie Registrierungseintrags in folgendem Verzeichnis:  
  
     [HKLM\SOFTWARE\Microsoft \Visual Studio\\*\<Visual Studio-Version >*\FontAndColors\\*\<Kategorie >*]  
  
     *\<Kategorie >* der nicht lokalisierte Name der Kategorie.  
  
2.  Füllen Sie die Registrierung, um die vordefinierten Schriftarten und Farbschemas mit vier Werten verwenden:  
  
    |Name|Typ|Daten|Beschreibung|  
    |----------|----------|----------|-----------------|  
    |Kategorie|REG_SZ|GUID|Eine beliebige GUID, die eine Kategorie identifiziert, die die vordefinierten Schriftarten und Farbschemas enthält.|  
    |Package|REG_SZ|GUID|{F5E7E71D-1401-11D1-883B-0000F87579D2}<br /><br /> Diese GUID wird von allen VSPackages verwendet, die die Standardkonfigurationen für Schriftart und Farbe zu verwenden.|  
    |"NameID"|REG_DWORD|ID|Die Ressourcen-ID, der einen lokalisierbaren Kategorienamen im VSPackage.|  
    |ToolWindowPackage|REG_SZ|GUID|Die GUID der VSPackage-Implementierung der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> Schnittstelle.|  
  
3.  
  
### <a name="to-initiate-the-use-of-system-provided-fonts-and-colors"></a>So initiieren Sie die Verwendung von vom System bereitgestellte Schriftarten und Farben  
  
1.  Erstellen Sie eine Instanz von der `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer` -Schnittstelle als Teil der Implementierung und die Initialisierung des Fensters.  
  
2.  Rufen Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer.GetPropertyCategory%2A> Methode zum Abrufen einer Instanz der `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer` Schnittstelle, die entsprechend dem aktuellen <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> Instanz.  
  
3.  Rufen Sie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A> zweimal.  
  
    -   Rufen Sie einmal mit `VSEDITPROPID_ViewGeneral_ColorCategory`als Argument.  
  
    -   Rufen Sie einmal mit `VSEDITPROPID_ViewGeneral_FontCategory` als Argument.  
  
     Legt fest, und macht die Standarddienste für Schriftarten und Farben als Eigenschaft des Fensters.  
  
## <a name="example"></a>Beispiel  
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
  
## <a name="see-also"></a>Siehe auch  
 [Verwenden von Schriftarten und Farben](../extensibility/using-fonts-and-colors.md)   
 [Abrufen von Informationen zur Schriftart und Farbe für die farbliche Kennzeichnung von Text](../extensibility/getting-font-and-color-information-for-text-colorization.md)   
 [Zugriff auf gespeicherte Schriftart- und Farbeinstellungen](../extensibility/accessing-stored-font-and-color-settings.md)   
 [Schriftart und Farbe (Übersicht)](../extensibility/font-and-color-overview.md)