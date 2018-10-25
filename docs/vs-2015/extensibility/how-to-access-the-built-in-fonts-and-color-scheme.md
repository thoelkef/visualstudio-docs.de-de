---
title: 'Vorgehensweise: Zugreifen auf die integrierten Schriftarten und Farbschemas | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- fonts, accessing built-in
- font and color control [Visual Studio SDK], categories
- colors, accessing built-in schemes
ms.assetid: 6905845e-e88e-4805-adcf-21da39108ec7
caps.latest.revision: 24
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b4938057514071836fefbca6988cf05a6399126e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49811892"
---
# <a name="how-to-access-the-built-in-fonts-and-color-scheme"></a>Vorgehensweise: Zugreifen auf die integrierten Schriftarten und Farbschemas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die integrierte Entwicklungsumgebung (IDE) von Visual Studio verfügt über ein Schema von Schriftarten und Farben, die im Editor-Fenster zugeordnet ist. Sie erreichen dieses Schema über die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> Schnittstelle.  
  
 Um integrierte Schriftarten und Farbschema zu verwenden, müssen eine VSPackage ein:  
  
- Definieren Sie eine Kategorie, um den Standarddienst für Schriftarten und Farben verwenden.  
  
- Registrieren Sie die Kategorie, mit der standardmäßigen Schriftarten und Farben.  
  
- Empfehlen Sie, dass ein bestimmtes Fenster die Kategorien und integrierte Anzeigeelementen, indem verwendet der IDE die `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer` und `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer` Schnittstellen.  
  
  Die IDE verwendet die resultierende Kategorie als ein Handle für das Fenster an. Die Kategorie der Name wird angezeigt, der **Einstellungen anzeigen für:** Dropdown-Listenfeld in der **Schriftarten und Farben** Eigenschaftenseite.  
  
### <a name="to-define-a-category-using-built-in-fonts-and-colors"></a>Definieren Sie eine Kategorie mit integrierten Schriftarten und Farben  
  
1. Erstellen Sie eine beliebige GUID.  
  
    Diese GUID wird zur eindeutigen Identifizierung eine Kategorie verwendet<strong>.</strong> Diese Kategorie wird wiederverwendet, die IDE Standard-Schriftarten und Farben-Spezifikation.  
  
   > [!NOTE]
   >  Beim Abrufen von Daten von Schriftart und Farbe mit der <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents> oder andere Schnittstellen, VSPackages verwenden diese GUID, um integrierte Informationen zu verweisen.  
  
2. Eine Zeichenfolgentabelle in die VSPackage Ressourcendatei (.rc), muss dem Kategorienamen hinzugefügt werden, damit sie lokalisiert werden kann, je nach Bedarf, wenn Sie in der IDE angezeigt.  
  
    Weitere Informationen finden Sie unter [hinzufügen oder Löschen von Zeichenfolgen](http://msdn.microsoft.com/library/077077b4-0f4b-4633-92d6-60b321164cab).  
  
### <a name="to-register-a-category-using-built-in-fonts-and-colors"></a>Registrieren Sie eine Kategorie mit integrierten Schriftarten und Farben  
  
1.  Erstellen Sie eine besondere Art von Kategorie-Registrierungseintrag an folgendem Speicherort:  
  
     ["HKLM\Software\Microsoft" \Visual Studio\\*\<Visual Studio-Version >* \FontAndColors\\*\<Kategorie >*]  
  
     *\<Kategorie >* ist der nicht lokalisierte Name der Kategorie.  
  
2.  Füllen Sie die Registrierung, um die vordefinierten Schriftarten und Farbschemas mit vier Werten verwenden:  
  
    |name|Typ|Daten|Beschreibung|  
    |----------|----------|----------|-----------------|  
    |Kategorie|REG_SZ|GUID|Eine beliebige GUID, die eine Kategorie identifiziert, die die vordefinierten Schriftart- und Farbschema enthält.|  
    |Package|REG_SZ|GUID|{F5E7E71D-1401-11D1-883B-0000F87579D2}<br /><br /> Diese GUID wird von allen VSPackages verwendet, die die Standardkonfigurationen für Schriftart und Farbe zu verwenden.|  
    |"NameID"|REG_DWORD|Id|Die Ressourcen-ID einer lokalisierbaren Kategorienamen im VSPackage.|  
    |ToolWindowPackage|REG_SZ|GUID|Die GUID der VSPackage-Implementierung der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> Schnittstelle.|  
  
3.  
  
### <a name="to-initiate-the-use-of-system-provided-fonts-and-colors"></a>Um die Verwendung von vom System bereitgestellten Schriftarten und Farben zu initiieren.  
  
1. Erstellen Sie eine Instanz von der `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer` -Schnittstelle als Teil der Implementierung und die Initialisierung des Fensters.  
  
2. Rufen Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer.GetPropertyCategory%2A> Methode zum Abrufen einer Instanz der `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer` Schnittstelle, die entsprechend dem aktuellen <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> Instanz.  
  
3. Rufen Sie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A> zweimal.  
  
   - Rufen Sie einmal mit `VSEDITPROPID_ViewGeneral_ColorCategory`als Argument.  
  
   - Rufen Sie einmal mit `VSEDITPROPID_ViewGeneral_FontCategory` als Argument.  
  
     Dies legt fest, und stellt die Standarddienste für Schriftarten und Farben als Eigenschaft des Fensters.  
  
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
 [Übersicht: Schriftart und Farben](../extensibility/font-and-color-overview.md)

