---
title: "Gewusst wie: Unterst&#252;tzen der Drag &amp; Drop-Funktionalit&#228;t der Toolbox | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Drag & Drop, Unterstützung in der Toolbox"
  - "Toolbox [Visual Studio SDK], Client"
  - "Toolbox [Visual Studio SDK], Drag & Drop"
ms.assetid: 2f73a03c-1eb1-4b88-9c1b-d63ba0e2ac90
caps.latest.revision: 18
caps.handback.revision: 18
manager: "douge"
---
# Gewusst wie: Unterst&#252;tzen der Drag &amp; Drop-Funktionalit&#228;t der Toolbox
> [!NOTE]
>  Die empfohlene Methode zum Hinzufügen benutzerdefinierter Steuerelemente zur Toolbox ist die Verwendung der Vorlagen für Toolbox\-Steuerelemente, die im Lieferumfang des Visual Studio 10 SDK enthalten sind und Drag & Drop unterstützen. Dieses Thema wird nur aus Gründen der Abwärtskompatibilität und für die Arbeit mit vorhandenen Steuerelementen beibehalten.  
>   
>  Weitere Informationen zum Erstellen von Toolbox\-Steuerelementen mithilfe der Vorlagen finden Sie unter [Gewusst wie: Erstellen eines Toolbox\-Steuerelements, das Windows Forms verwendet](../misc/how-to-create-a-toolbox-control-that-uses-windows-forms.md) und [Erstellen ein WPF\-Toolbox\-Steuerelement](../extensibility/creating-a-wpf-toolbox-control.md).  
  
 VSPackages müssen die Drag & Drop\-Unterstützung implementieren, wenn sie **Toolbox**\-Steuerelemente in Dokumentansichten verwenden sollen \(z. B. Editoren oder Designer\).  
  
 Alle von <xref:System.Windows.Forms.Control?displayProperty=fullName> abgeleiteten [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]\-Objekte bieten standardmäßig automatisch und offensichtlich die Unterstützung für die Verwendung von **Toolbox**\-Steuerelementen. Daher sind die unten beschriebenen Verfahren nicht erforderlich. Die grundlegende Funktionalität kann durch Erstellen eines Designers erweitert werden.  
  
 Weitere Informationen finden Sie unter [Übersicht über Windows Forms](../Topic/Windows%20Forms%20Overview.md) und [Extending Design\-Time Support](../Topic/Extending%20Design-Time%20Support.md).  
  
### So implementieren Sie die grundlegende Drag & Drop\-Funktionalität  
  
1.  Stellen Sie die Drag & Drop\-Unterstützung durch Implementieren von <xref:Microsoft.VisualStudio.OLE.Interop.IDropTarget> für ein Ansichtsobjekt bereit. Dadurch erhält die Ansicht die Drag & Drop\-OLE\-Funktionalität sowie die Serialisierung des Steuerelements.  
  
     Weitere Informationen zum Implementieren von Drag & Drop\-Funktionen finden Sie unter [Drag & Drop \(OLE\)](/visual-cpp/mfc/drag-and-drop-ole).  
  
     Ablegevorgänge können entweder Zwischenablageelemente oder Steuerelemente umfassen, die in einem Designer abgelegt werden. Informationen zu den Standardformaten der Zwischenablage, die von der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] **Toolbox** unterstützt werden, finden Sie unter [Erweitern der Toolbox](../misc/extending-the-toolbox.md).  
  
2.  Stellen Sie eine grundlegende Implementierung der <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser>\-Schnittstelle für eine Dokumentenansicht bereit.  
  
     Wenn ein Benutzer versucht, ein Toolbox\-Steuerelement in eine Ansicht zu ziehen, fragt die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Shell das VSPackage der Ansicht ab, um zu überprüfen, ob es die <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser>\-Schnittstelle implementiert.  
  
    1.  Implementieren Sie <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser.IsSupported%2A>, um <xref:Microsoft.VisualStudio.VSConstants.S_OK> für die **Toolbox**\-Formate zurückzugeben, die vom Ablageziel unterstützt werden. Im folgenden Beispiel wird überprüft, ob das Datenobjekt im benutzerdefinierten Format der Zwischenablage vorliegt \(`CF_CUSTOM_FORMAT`\) und ob es sich bei dem Objekt um ein ActiveX\-Steuerelement handelt.  
  
        ```cpp#  
        STDMETHODIMP CustTbxUser::IsSupported(IDataObject* pDO) { HRESULT hr; STGMEDIUM stm; if (!pDO) return E_POINTER; // Determine if the data object is in the Custom clip board format // fetc is the dialog editor toolbox item template. FORMATETC fetc = { m_CF_CUSTOM_FORMAT, //Value set with RegisterClipboardFormat NULL, DVASPECT_CONTENT, // DVASCPECT_ICON might be better -1, TYMED_HGLOBAL }; if (FAILED(hr = pDO->GetData(&fetc, &stm))) { // Determine if the object is in the class-id clipboard format ... this // would be the case if the control is an activeX toolbox item. FORMATETC xfetc = { m_CF_CLSID, NULL, DVASPECT_CONTENT, // DVASCPECT_ICON might be better -1, TYMED_HGLOBAL }; if (SUCCEEDED(hr = pDO->GetData(&xfetc,&stm))) { USES_CONVERSION; GUID guid; LPSTR pData = (LPSTR)GlobalLock(stm.hGlobal); if (pData) { // Convert from the string format to a binary GUID. if (CLSIDFromString(A2W(pData), &guid) != S_OK) return E_FAIL; // HTML data objects could have CLSID format ... so any data object could // be returned as a NULL guid ... fail on null guid, obviously they are // not active X controls. if (guid == GUID_NULL) return E_FAIL; } } } return hr; }  
        ```  
  
         Diese Informationen werden von der IDE beim ersten Laden des Fensters einer Ansicht und bei jeder Aktivierung des Fensters einer Ansicht nach der Zurücksetzung der **Toolbox** durch einen Benutzer über das Dialogfeld **Toolbox anpassen** der IDE überprüft. In der Regel werden von der **Toolbox** keine nicht unterstützten **Toolbox**\-Elemente angezeigt.  
  
         Benutzer können eine Option festlegen, dass alle Seiten der Toolbox jederzeit angezeigt werden. In diesem Fall wird der Editor nicht von der Umgebung nach <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser.IsSupported%2A> abgefragt.  
  
    2.  Nachdem eine <xref:Microsoft.VisualStudio.OLE.Interop.IDropTarget>\-Implementierung \(wie die oben beschriebene\) eine abgelegte Komponente erfolgreich behandelt hat, muss das Ansichtsobjekt die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Umgebung durch Aufrufen von <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2.DataUsed%2A> davon in Kenntnis setzen.  
  
     Bei Bedarf kann ein VSPackage die Drag & Drop\-Unterstützung erweitern, indem seine <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser>\-Implementierung erweitert wird.  
  
3.  Eine <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser>\-Implementierung kann das Ziehen von **Toolbox**\-Elementen in ein Fenster eher durch Auswählen als durch Mausaktionen unterstützen. Das bedeutet, dass ein Element gezogen wird, wenn ein Benutzer entweder auf ein **Toolbox**\-Element doppelklickt oder nur einfach klickt und dann die EINGABETASTE drückt  Gehen Sie dazu wie folgt vor:  
  
    1.  Implementieren Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser.ItemPicked%2A>\-Methode.  
  
         Diese von der IDE aufgerufene Methode wird durch Klicken oder durch Drücken der EINGABETASTE ausgewählt.  
  
         Die Methode sollte das **Toolbox**\-Element dann im Zielfenster einfügen.  
  
    2.  Die Methode sollte <xref:Microsoft.VisualStudio.VSConstants.S_FALSE> zurückgeben, wenn Sie die Implementierung durch Auswahl nicht unterstützen möchten.  
  
         Im folgenden Beispiel wird durch die Implementierung der <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser.ItemPicked%2A>\-Methode überprüft, ob das ausgewählte Objekt unterstützt wird. Wenn dies der Fall ist, wird es im Code deserialisiert:  
  
        ```cpp#  
        STDMETHODIMP CustTbxUser::ItemPicked(IDataObject* pDataObject) { if (!pDataObject) return E_POINTER; UINT nIDTool; if (IsSupported(pDataObject) == S_OK) { SetToolCursor(); m_pDataObject = pDataObject; nIDTool = DeserializeObject(); // Get the focus back m_pResObject->m_spWndFrame->Show(); return S_OK; } }  
        ```  
  
4.  Führen Sie die folgenden Schritte aus, um sicherzustellen, dass für Ihre Anwendung der richtige Fokus beibehalten wird:  
  
    1.  Wenn das Editorfenster zwei verschiedene Bereiche implementiert \(nicht zwei verschiedene Ansichten\), rufen Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2.UpdateToolboxUI%2A>\-Methode auf, wenn Sie im Editorfenster die Bereichsaktivierung wechseln. Nur Ihnen ist bekannt, wann in Ihrem Fenster Aktivierungsänderungen auftreten.  
  
    2.  Sie müssen die <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A>\-Methode für die Komponente aufrufen, um das Fenster ordnungsgemäß zu aktivieren und sicherzustellen, dass das Befehlsrouting ordnungsgemäß aktualisiert wird. Diese Aktion muss ausgeführt werden, wenn Sie den Fokus auf ein Komponentenfenster setzen, z. B. auf einen Editor, das mithilfe eines Drag & Drop\-Vorgangs erstellt oder geändert wurde, der die Toolbox einbezieht.  
  
 Möglicherweise muss ein VSPackage in einen Ziehvorgang eingreifen und das abgelegte Element über die <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxActiveUserHook>\-Schnittstelle modifizieren.  
  
 Anstatt z. B. ein neues **Toolbox**\-Steuerelement explizit zur **Toolbox** hinzuzufügen, kann ein VSPackage eine Standard\-**Toolbox** beim Ablegen abfangen und sie durch eine benutzerdefinierte Implementierung ersetzen.  
  
### So ändern Sie Toolbox\-Steuerelemente dynamisch  
  
1.  Implementieren Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxActiveUserHook>\-Methode.  
  
     Sobald ein **Toolbox**\-Element ausgewählt oder abgelegt wird, fragt die **Toolbox** das Ablageziel ab, um zu überprüfen, ob es die <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxActiveUserHook>\-Schnittstelle unterstützt und die <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxActiveUserHook.InterceptDataObject%2A>\-Methode aufruft.  
  
2.  Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxActiveUserHook.InterceptDataObject%2A>\-Methode muss ein neues <xref:Microsoft.VisualStudio.OLE.Interop.IDataObject>\-Objekt zurückgeben, das anstelle des ursprünglichen <xref:Microsoft.VisualStudio.OLE.Interop.IDataObject> verwendet wird.  
  
     Wenn das Ablageziel das Datenobjekt nicht außer Kraft setzen muss, sollte es eine Eingabe zurückgeben.  
  
 Ein VSPackage kann es Benutzern ermöglichen, die Inhalte der Zwischenablage durch Drücken von STRG\+UMSCHALT\+V zu durchlaufen.  
  
### So unterstützen Sie einen Zwischenablagering  
  
1.  Verwenden Sie Folgendes, um einen Handler für den `CMDIDPasteNextTBXCBItem`\-Befehl zu implementieren:  
  
    -   <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> für VSPackages, die auf Interopassemblys basieren.  
  
    -   <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> für VSPackages, die auf dem Managed Package Framework basieren.<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxClipboardCycler>\-Schnittstelle.  
  
2.  Implementieren Sie im Befehlshandler die <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxClipboardCycler.AreDataObjectsAvailable%2A>\-Methode, um zu ermitteln, ob Zwischenablageobjekte vorhanden sind, die durchlaufen werden können.  
  
    1.  Wenn in der Toolbox\-Zwischenablage keine Elemente vorhanden sind, überprüft die Umgebung die Systemzwischenablage auf vorhandene Elemente.  
  
    2.  Wenn sich Elemente in der Zwischenablage des Systems, aber nicht in der Zwischenablage der Toolbox befinden, wird der Zwischenablagering mit Systemelementen gefüllt.  
  
    3.  Die Implementierung ruft die <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxClipboardCycler.GetAndSelectNextDataObject%2A>\-Methode auf, um das nächste Element in der Liste auszuwählen.  
  
    4.  Rufen Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxClipboardCycler.BeginCycle%2A>\-Methode auf, um an den Anfang des Zwischenablagezyklus zurückzukehren.  
  
## Siehe auch  
 [Erweitern der Toolbox](../misc/extending-the-toolbox.md)   
 [Gewusst wie: Bereitstellen von benutzerdefinierten Werkzeugkastenelementen mithilfe von Interopassemblys](../misc/how-to-provide-custom-toolbox-items-by-using-interop-assemblies.md)   
 [Erweiterte Toolbox\-Steuerelemententwicklung](../misc/advanced-toolbox-control-development.md)   
 [Registrieren von Funktionen zur Toolbox\-Unterstützung](../misc/registering-toolbox-support-features.md)   
 [Verwalten der Toolbox](../misc/managing-the-toolbox.md)