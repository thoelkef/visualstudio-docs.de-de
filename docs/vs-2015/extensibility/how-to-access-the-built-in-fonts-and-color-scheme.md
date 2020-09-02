---
title: 'Gewusst wie: Zugreifen auf die integrierten Schriftarten und das Farbschema | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- fonts, accessing built-in
- font and color control [Visual Studio SDK], categories
- colors, accessing built-in schemes
ms.assetid: 6905845e-e88e-4805-adcf-21da39108ec7
caps.latest.revision: 24
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a43fb3a22ecb2d04542eacf07bf883590868b75b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65685311"
---
# <a name="how-to-access-the-built-in-fonts-and-color-scheme"></a>Vorgehensweise: Zugriff auf integrierte Schriftarten und Farbschemas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die integrierte Entwicklungsumgebung (Integrated Development Environment, IDE) von Visual Studio verfügt über ein Schema mit Schriftarten und Farben, die dem Editor Fenster zugeordnet sind. Sie können über die-Schnittstelle auf dieses Schema zugreifen <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> .  
  
 Für ein VSPackage muss Folgendes verwendet werden, um das integrierte Schriftarten-und Farbschema zu verwenden:  
  
- Definieren Sie eine Kategorie, die mit dem Standard Dienst für Schriftarten und Farben verwendet werden soll.  
  
- Registrieren Sie die Kategorie mit dem Standard Server für Schriftarten und Farben.  
  
- Hiermit wird der IDE mitgeteilt, dass ein bestimmtes Fenster die integrierten Anzeigeelemente und Kategorien mithilfe der `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer` -und- `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer` Schnittstellen verwendet.  
  
  Die IDE verwendet die resultierende Kategorie als Handle für das Fenster. Der Name der Kategorie wird im Dropdown Feld **Einstellungen anzeigen für:** auf der Eigenschaften Seite **Schriftarten und Farben** angezeigt.  
  
### <a name="to-define-a-category-using-built-in-fonts-and-colors"></a>So definieren Sie eine Kategorie mithilfe integrierter Schriftarten und Farben  
  
1. Erstellen Sie eine beliebige GUID.  
  
    Diese GUID wird verwendet, um eine Kategorie eindeutig zu identifizieren<strong>.</strong> Diese Kategorie verwendet die Standardspezifikation für Schriftarten und Farben der IDE erneut.  
  
   > [!NOTE]
   > Wenn Sie Schriftart-und Farbdaten mit den- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents> oder anderen Schnittstellen abrufen, verwenden VSPackages diese GUID, um auf integrierte Informationen zu verweisen.  
  
2. Der Name der Kategorie muss einer Zeichen folgen Tabelle in der Ressourcen Datei (RC-Datei) des VSPackages hinzugefügt werden, damit Sie nach Bedarf lokalisiert werden kann, wenn Sie in der IDE angezeigt wird.  
  
    Weitere Informationen finden Sie unter [Hinzufügen oder Löschen einer Zeichenfolge](https://msdn.microsoft.com/library/077077b4-0f4b-4633-92d6-60b321164cab).  
  
### <a name="to-register-a-category-using-built-in-fonts-and-colors"></a>So registrieren Sie eine Kategorie mithilfe integrierter Schriftarten und Farben  
  
1. Erstellen Sie einen besonderen Typ von Kategorien Registrierungs Eintrag an folgendem Speicherort:  
  
     [HKLM\SOFTWARE\Microsoft \Visual Studio \\ *\<Visual Studio version>* \Fontandcolors \\ *\<Category>* ]  
  
     *\<Category>* der nicht lokalisierte Name der Kategorie.  
  
2. Füllen Sie die Registrierung auf, um die Schriftarten und das Farbschema mit vier Werten zu verwenden:  
  
    |Name|Typ|Daten|BESCHREIBUNG|  
    |----------|----------|----------|-----------------|  
    |Category|REG_SZ|GUID|Eine beliebige GUID, die eine Kategorie identifiziert, die das Aktien Schriftart-und Farbschema enthält.|  
    |Paket|REG_SZ|GUID|F5E7E71D-1401-11d1-883B-0000F87579D2<br /><br /> Diese GUID wird von allen VSPackages verwendet, die die standardmäßigen Schriftart-und farbkonfigurationen verwenden.|  
    |NameID|REG_DWORD|id|Die Ressourcen-ID eines lokalisierbaren Kategorienamens im VSPackage.|  
    |Toolwindowpackage|REG_SZ|GUID|Die GUID des VSPackage, das die- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> Schnittstelle implementiert.|  
  
3. 
  
### <a name="to-initiate-the-use-of-system-provided-fonts-and-colors"></a>So initiieren Sie die Verwendung der vom System bereitgestellten Schriftarten und Farben  
  
1. Erstellen Sie `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer` im Rahmen der Implementierung und Initialisierung des Fensters eine Instanz der-Schnittstelle.  
  
2. Rufen Sie die- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer.GetPropertyCategory%2A> Methode auf, um eine Instanz der- `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer` Schnittstelle zu erhalten, die der aktuellen <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> Instanz entspricht.  
  
3. Zweimal aufgerufen werden <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A> .  
  
   - Ruft einmal mit `VSEDITPROPID_ViewGeneral_ColorCategory` als Argument auf.  
  
   - Ruft einmal mit `VSEDITPROPID_ViewGeneral_FontCategory` als Argument auf.  
  
     Dadurch werden die Standarddienste für Schriftarten und Farben als Eigenschaft des Fensters festgelegt und verfügbar gemacht.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die Verwendung integrierter Schriftarten und Farben initiiert.  
  
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
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwenden von Schriftarten und Farben](../extensibility/using-fonts-and-colors.md)   
 [Informationen zu Schriftart und Farbe für die farbliche Kennzeichnung von Text](../extensibility/getting-font-and-color-information-for-text-colorization.md)   
 [Zugreifen auf gespeicherte Schriftart-und Farbeinstellungen](../extensibility/accessing-stored-font-and-color-settings.md)   
 [Übersicht: Schriftart und Farben](../extensibility/font-and-color-overview.md)
