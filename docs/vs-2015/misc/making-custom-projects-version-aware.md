---
title: Bewirken, dass benutzerdefinierte Projekte Versionsfähig | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
ms.assetid: 5233d3ff-6e89-4401-b449-51b4686becca
caps.latest.revision: 33
manager: jillfra
ms.openlocfilehash: 3118ce72cd75baaf15fc66eedc5f2cd48c6f43d6
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60096594"
---
# <a name="making-custom-projects-version-aware"></a>Bewirken, dass benutzerdefinierte Projekte versionsfähig werden
In Ihrem benutzerdefinierte Projektsystem können Sie zulassen, dass Projekte dieses Typs in mehreren Versionen von Visual Studio geladen werden. Sie können aber auch verhindern, dass Projekte dieses Typs in einer früheren Version von Visual Studio geladen werden. Außerdem können Sie für dieses Projekt ermöglichen, sich selbst für eine neuere Version zu identifizieren für den Fall, dass das Projekt repariert, konvertiert oder als veraltet deklariert werden muss.  
  
## <a name="allowing-projects-to-load-in-multiple-versions"></a>Zulassen, dass Projekte in mehreren Versionen geladen werden können  
 Sie können die meisten Projekte, die in [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] mit SP1 oder höher erstellt wurden, so ändern, dass sie in mehreren Versionen funktionieren.  
  
 Bevor ein Projekt geladen wird, ruft Visual Studio die <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory4.UpgradeProject_CheckOnly%2A>-Methode auf, um zu ermitteln, ob ein Upgrade für das Projekt durchgeführt werden kann. Ist dies der Fall, legt die `UpgradeProject_CheckOnly`-Methode ein Flag fest, das einen späteren Aufruf der <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>-Methode bewirkt, um ein Upgrade für das Projekt durchzuführen. Da für inkompatible Projekte kein Upgrade durchgeführt werden kann, muss `UpgradeProject_CheckOnly` zunächst auf Projektkompatibilität prüfen, wie dies im vorherigen Abschnitt beschrieben ist.  
  
 Sie als der Autor eines Projektsystems implementieren `UpgradeProject_CheckOnly` (aus der `IVsProjectUpgradeViaFactory4` -Schnittstelle), um Benutzern Ihres Projektsystems eine Upgradeprüfung bereitzustellen. Wenn ein Benutzer ein Projekt öffnet, wird diese Methode aufgerufen, um festzustellen, ob ein Projekt repariert werden muss, bevor es geladen wird. Die möglichen Upgradeanforderungen werden in `VSPUVF_REPAIRFLAGS`aufgelistet, und sie enthalten folgende Möglichkeiten:  
  
1. `SPUVF_PROJECT_NOREPAIR`: Ist keine Reparatur erforderlich.  
  
2. `VSPUVF_PROJECT_SAFEREPAIR`: Macht das Projekt mit einer früheren Version kompatibel ohne die Probleme, die möglicherweise in den vorherigen Versionen des Produkts aufgetreten.  
  
3. `VSPUVF_PROJECT_UNSAFEREPAIR`: Macht das Projekt rückwärtskompatibel aber einige Risiken, das Sie festgestellt haben, können Probleme mit früheren Versionen des Produkts. Beispielsweise wird das Projekt nicht kompatibel sein, wenn es von verschiedenen SDK-Versionen abhängt.  
  
4. `VSPUVF_PROJECT_ONEWAYUPGRADE`: Macht das Projekt mit einer früheren Version nicht kompatibel.  
  
5. `VSPUVF_PROJECT_INCOMPATIBLE`: Gibt an, dass die aktuelle Version dieses Projekt nicht unterstützt.  
  
6. `VSPUVF_PROJECT_DEPRECATED`: Gibt an, dass dieses Projekt nicht mehr unterstützt wird.  
  
> [!NOTE]
>  Um Verwirrung zu vermeiden, sollten Sie Upgradeflags nicht kombinieren, wenn Sie diese festlegen. Beispielsweise sollten Sie keinen mehrdeutigen Upgradestatus wie etwas `VSPUVF_PROJECT_SAFEREPAIR | VSPUVF_PROJECT_DEPRECATED`erstellen.  
  
 In einer Projektkonfiguration kann die Funktion `UpgradeProjectFlavor_CheckOnly` aus der `IVsProjectFlavorUpgradeViaFactory2` -Schnittstelle implementiert werden. Damit diese Funktion funktioniert, muss sie von der bereits erwähnten `IVsProjectUpgradeViaFactory4.UpgradeProject_CheckOnly` -Implementierung aufgerufen werden. Dieser Aufruf ist im Visual Basic- oder C#-Basisprojektsystem bereits implementiert. Anhand des Ergebnisses dieser Funktion können Projektkonfigurationen ebenfalls die Upgradeanforderungen eines Projekts ermitteln, zusätzlich zu dem, was das Basisprojektsystem ermittelt hat. Ims Dialogfeld für Kompatibilität wird die schwerwiegendere der beiden Anforderungen angezeigt.  
  
 Wenn Visual Studio eine Upgradeprüfung ausführt, stellt es nicht wie in früheren Versionen einen NULL-Wert, sondern eine Protokollierung bereit. Die Protokollierung ermöglicht es Projektsystemen und -konfigurationen, zusätzliche Informationen bereitzustellen, anhand denen Sie die Art der Änderungen verstehen können, die erforderlich sind, damit Ihre älteren Projekten ordnungsgemäß geladen werden. Es wird empfohlen, dass Sie die Protokollierung verwenden, um weitere Informationen bereitzustellen, statt Dialogfelder zu verwenden. Weitere Informationen finden Sie weiter unten in diesem Thema unter [The Upgrade Logger](../misc/making-custom-projects-version-aware.md#BKMK_UpgradeLogger) .  
  
 Für verwaltete Implementierungen sind die Projektupgradeschnittstellen in der Interopassembly „Microsoft.VisualStudio.Shell.Interop.11.0.dll“ verfügbar.  
  
 Die `UpgradeProject` -Methode kann ermitteln, ob die von ihr vorgenommenen Änderungen dazu führen, dass es nicht mehr möglich ist, das Projekt in einer früheren Version von Visual Studio zu laden. Ist dies der Fall, kennzeichnet die Methode das Projekt als nicht kompatibel. Wenn Sie wissen möchten, wie ein Projekt als nicht kompatibel gekennzeichnet wird, lesen Sie [Marking a Project as Incompatible](../misc/making-custom-projects-version-aware.md#BKMK_Incompat) weiter oben in diesem Thema. Es empfiehlt sich, dass Sie das Projekt, nachdem dieses Dialogfeld angezeigt wurde, direkt durch Aufrufen der Methode `IVsAppCompat.BreakAssetCompatibility` als nicht kompatibel kennzeichnen, statt zuerst die `IVsAppCompat.AskForUserConsentToBreakAssetCompat` -Methode aufzurufen, denn das Dialogfeld muss nicht zweimal angezeigt werden.  
  
 Es folgt ein Beispiel, in dem die kompatibilitätsbezogene Vorgehensweise zusammengefasst ist. Wurde ein Projekt in einer früheren Version erstellt, und stellt die aktuelle Version fest, dass ein Upgrade erforderlich ist, zeigt Visual Studio ein Dialogfeld an, in dem der Benutzer gebeten wird, die Berechtigung zum Vornehmen der Änderungen zu erteilen. Stimmt der Benutzer zu, wird das Projekt geändert und dann geladen. Wird die Projektmappe nun geschlossen und in der früheren Version wieder geöffnet, ist das auf die höhere Version aktualisierte Projekt nicht kompatibel und wird nicht geladen. Gab es für das Projekt nur eine erforderliche Reparatur (anstelle eines Upgrades), wird das reparierte Projekt weiterhin in beiden Versionen geöffnet.  
  
## <a name="BKMK_Incompat"></a> Kennzeichnen eines Projekt als nicht kompatibel  
 Sie können ein Projekt als nicht kompatibel mit früheren Versionen von Visual Studio kennzeichnen.  Nehmen Sie beispielsweise an, Sie erstellen ein Projekt, in dem eine .NET Framework 4.5-Funktion verwendet wird. Da dieses Projekt nicht in [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)]erstellt werden kann, können Sie es als nicht kompatibel kennzeichnen, um zu verhindern, dass diese Version versucht, das Projekt zu laden.  
  
 Die Komponente, aus der die nicht kompatible Funktion hinzufügt wurde, ist dafür zuständig, das Projekt als nicht kompatibel zu kennzeichnen. Die Komponente muss Zugriff auf die <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>-Schnittstelle haben, die den betroffenen Projekten entspricht.  
  
#### <a name="to-mark-a-project-as-incompatible"></a>So kennzeichnen Sie ein Projekt als nicht kompatibel  
  
1. Rufen Sie in der Komponente eine `IVsAppCompat` -Schnittstelle aus dem globalen Dienst „SVsSolution“ ab.  
  
     Weitere Informationen finden Sie unter <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>.  
  
2. Rufen Sie in der Komponente die `IVsAppCompat.AskForUserConsentToBreakAssetCompat`-Methode auf, und übergeben Sie dieser ein Array von `IVsHierarchy` -Schnittstellen, die die betroffenen Projekte darstellen.  
  
     Diese Methode hat die folgende Signatur:  
  
    ```  
    HRESULT AskForUserConsentToBreakAssetCompat([in] SAFEARRAY(IVsHierarchy*) sarrProjectHierarchies)  
  
    ```  
  
     Wenn Sie diesen Code implementieren, wird ein Dialogfeld zur Projektkompastibilität angezeigt. In dem ein Dialogfeld wird Benutzer aufgefordert, die Berechtigung zu erteilen, alle angegebenen Projekte als nicht kompatibel zu kennzeichnen. Stimmt der Benutzer zu, gibt `AskForUserConsentToBreakAssetCompat` den Wert `S_OK`zurück. Andernfalls gibt `AskForUserConsentToBreakAssetCompat` den Wert `OLE_E_PROMPTSAVECANCELLED`zurück.  
  
    > [!WARNING]
    >  In den meisten Fällen enthält das `IVsHierarchy` -Array nur ein Element.  
  
3. Wenn `AskForUserConsentToBreakAssetCompat` den Wert `S_OK`zurückgibt, nimmt die Komponente die Änderungen vor, die die Kompatibilität beseitigen, oder die Komponente akzeptiert diese Änderungen.  
  
4. Rufen Sie in Ihrer Komponente die `IVsAppCompat.BreakAssetCompatibility` -Methode für jedes Projekt, das Sie als nicht kompatibel kennzeichnen möchten. Die Komponente kann den Wert des Parameters `lpszMinimumVersion` auf eine bestimmte mindestens erforderliche Version festlegen, sodass Visual Studio nicht gezwungen ist, die aktuelle Versionszeichenfolge in der Registrierung zu suchen. Diese Vorgehensweise verringert das Risiko, dass die Komponente zukünftig anhand des Werts, der zu diesem Zeitpunkt in der Registrierung steht, versehentlich einen höheren Wert festlegt. Würde dieser höhere Wert festgelegt, könnte Visual Studio das Projekt nicht öffnen.  
  
     Diese Methode hat die folgende Signatur:  
  
    ```  
    HRESULT BreakAssetCompatibility([in] IVsHierarchy * pProjHier), [in] LPCOLESTR lpszMinimumVersion);  
  
    ```  
  
     Wird `lpszMinimumVersion` in der Komponente auf NULL festgelegt, ruft die `BreakAssetCompatibility` -Methode die `IVsAppCompat.GetCurrentDesignTimeCompatVersion` -Methode auf, um eine Zeichenfolge abzurufen, die die aktuelle Version von Visual Studio darstellt.  
  
     Diese Methode hat die folgende Signatur:  
  
    ```  
    HRESULT GetCurrentDesignTimeCompatVersion([out] BSTR * pbstrCurrentDesignTimeCompatVersion)  
    ```  
  
     Anschließend ruft die BreakAssetCompatibility-Methode die `IVsHierarchy.SetProperty` -Methode auf, um die `VSHPROPID_MinimumDesignTimeCompatVersion` -Stammeigenschaft auf den Wert der Versionszeichenfolge festzulegen, die Sie im vorherigen Schritt abgerufen haben.  
  
     Weitere Informationen finden Sie unter <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A>.  
  
> [!IMPORTANT]
>  Sie müssen die `VSHPROPID_MinimumDesignTimeCompatVersion` -Eigenschaft implementieren, damit ein Projekt als kompatibel oder nicht kompatibel gekennzeichnet werden kann. Wird für das Projektsystem beispielsweise eine MSBuild-Projektdatei verwendet, fügen Sie der Projektdatei eine `<MinimumVisualStudioVersion>` -Buildeigenschaft hinzu, die denselben Wert hat wie die entsprechende `VSHPROPID_MinimumDesignTimeCompatVersion` -Eigenschaft.  
  
## <a name="detecting-whether-a-project-is-incompatible"></a>Ermitteln, ob ein Projekt nicht kompatibel ist  
 Für ein Projekt, das nicht mit der aktuellen Version von Visual Studio kompatibel ist, muss verhindert werden, dass es geladen wird. Darüber hinaus kann ein Projekt, das nicht kompatibel ist, weder ein Upgrade durchlaufen noch repariert werden. Daher muss ein Projekt zweimal auf Kompatibilität überprüft werden: erstmals, wenn es für ein Upgrade oder eine Reparatur berücksichtigt wird, und zweitens, bevor es geladen wird.  
  
 Um die Erkennung von Projektinkompatibilität zu aktivieren, müssen Sie die Methoden <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory4.UpgradeProject_CheckOnly%2A> und <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> implementieren. Ist ein Projekt nicht kompatibel, muss `UpgradeProject_CheckOnly` den Erfolgscode `VS_S_INCOMPATIBLEPROJECT`zurückgeben, und `CreateProject` muss den Fehlercode `VS_E_INCOMPATIBLEPROJECT`zurückgeben. Für ein Flavor-Projekt müssen Sie `IVsProjectFlavorUpgradeViaFactory2.UpgradeProjectFlavor_CheckOnly` anstelle von `IVsProjectUpgradeViaFactory4.UpgradeProject_CheckOnly`implementieren.  
  
 Ein Projektsystem wird als Flavor-Projektsystem bezeichnet, wenn auf ihm ein Web-, Office (VSTO)-, Silverlight- oder anderer Projekttyp aufsetzt. Ältere Projektsysteme, für die bereits `IVsProjectUpgradeViaFactory.UpgradeProject_CheckOnly` implementiert ist, und Flavor-Projektsysteme, für die bereits `IVsProjectFlavorUpgradeViaFactory.UpgradeProjectFlavor_CheckOnly` implementiert ist, werden weiterhin unterstützt. Die ältere Version von `IVsProjectUpgradeViaFactory.UpgradeProject_CheckOnly` hat die folgende Implementierungssignatur:  
  
```  
IVsProjectUpgradeViaFactory::UpgradeProject_CheckOnly(  
  
/* [in] */ BSTR bstrFileName,  
/* [in] */ IVsUpgradeLogger *pLogger,  
/* [out] */ BOOL *pUpgradeRequired,  
/* [out] */ GUID *pguidNewProjectFactory,  
/* [out] */ VSPUVF_FLAGS *pUpgradeProjectCapabilityFlags  
)  
```  
  
 Wird `pUpgradeRequired` von dieser Methode auf TRUE festgelegt, und gibt die Methode den Wert `S_OK`zurück, wird das Ergebnis als „Upgrade“ behandelt, weshalb die Methode ein Upgradeflag auf den Wert `VSPUVF_PROJECT_ONEWAYUPGRADE`festgelegt, der weiter unten in diesem Thema beschrieben wird. Der folgende Rückgabewerte werden unterstützt, wenn diese ältere Methode verwendet wird, allerdings nur, wenn `pUpgradeRequired` auf TRUE festgelegt ist:  
  
1. `VS_S_PROJECT_SAFEREPAIRREQUIRED`. Dieser Rückgabewert übersetzt den `pUpgradeRequired` -Wert in TRUE als Entsprechung zu `VSPUVF_PROJECT_SAFEREPAIR`, das weiter unten in diesem Thema beschrieben wird.  
  
2. `VS_S_PROJECT_UNSAFEREPAIRREQUIRED`. Dieser Rückgabewert übersetzt den `pUpgradeRequired` -Wert in TRUE als Entsprechung zu `VSPUVF_PROJECT_UNSAFEREPAIR`, das weiter unten in diesem Thema beschrieben wird.  
  
3. `VS_S_PROJECT_ONEWAYUPGRADEREQUIRED`. Dieser Rückgabewert übersetzt den `pUpgradeRequired` -Wert in TRUE als Entsprechung zu `VSPUVF_PROJECT_ONEWAYUPGRADE`, das weiter unten in diesem Thema beschrieben wird.  
  
   Die neuen Implementierungen in `IVsProjectUpgradeViaFactory4` und `IVsProjectFlavorUpgradeViaFactory2` ermöglichen es, den Migrationstyp genauer anzugeben.  
  
> [!NOTE]
>  Sie können das Ergebnis der Kompatibilitätsüberprüfung durch die `UpgradeProject_CheckOnly` -Methode zwischenspeichern, sodass es auch für den späteren Aufruf von `CreateProject`verwendet werden kann.  
  
 Wenn beispielsweise die Methoden `UpgradeProject_CheckOnly` und `CreateProject` , die für ein [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] mit SP1-Projektsystem geschrieben sind, eine Projektdatei auswerten und feststellen, dass die `<MinimumVisualStudioVersion>` -Buildeigenschaft den Wert „11.0“ hat, wird das Projekt von Visual Studio 2010 mit SP1 nicht geladen. Darüber hinaus würde der **Projektmappen-Navigator** angeben, dass das Projekt „nicht kompatibel“ ist, und würde es nicht laden.  
  
## <a name="BKMK_UpgradeLogger"></a> Die Upgrade-Protokollierung  
 Ein Aufruf von `IVsProjectUpgradeViaFactory::UpgradeProject` enthält eine `IVsUpgradeLogger` -Protokollierung. Diese sollte von Projektsystemen und -konfigurationen verwendet werden, um ausführliche Upgradeablaufverfolgung zur Problembehandlung bereitzustellen. Wird eine Warnung oder ein Fehler protokolliert, zeigt Visual Studio den Upgradebericht an.  
  
 Für das Schreiben in die Upgrade-Protokollierung sollten Sie die folgenden Richtlinien beachten:  
  
- Visual Studio ruft „Flush“ auf, nachdem das Upgrade für alle Projekte durchgeführt wurde. Rufen Sie „Flush“ nicht in Ihrem Projektsystem auf.  
  
- Die LogMessage-Funktion hat die folgenden Fehlerstufen (ErrorLevels):  
  
    - 0 steht für irgendeine Information, die Sie verfolgen möchten.  
  
    - 1 steht für eine Warnung.  
  
    - 2 steht für einen Fehler.  
  
    - 3 steht für das Berichts-Formatierungsprogramm. Wenn für Ihr Projekt das Upgrade durchgeführt wurde, protokollieren Sie das Wort „Converted“ einmal, und lokalisieren Sie dieses Wort nicht.  
  
- Erfordert ein Projekt weder eine Reparatur noch ein Upgrade, generiert Visual Studio die Protokolldatei nur, wenn das Projektsystem während der Methode „UpgradeProject_CheckOnly“ oder „UpgradeProjectFlavor_CheckOnly“ eine Warnung oder einen Fehler protokolliert hat.