---
title: Implementieren von Smart Host-Hilfsprogrammschnittstellen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Smart Host Helper Interfaces, implementing
ms.assetid: b9c44246-4d4d-469e-91be-00c8f5796fa5
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ba571f6ad66855c44902e06467889e2cae5b4555
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24571520"
---
# <a name="implementing-smart-host-helper-interfaces"></a>Implementieren von Smart Host-Hilfsprogrammschnittstellen
Die [IDebugDocumentHelper-Schnittstelle](../winscript/reference/idebugdocumenthelper-interface.md) vereinfacht das Erstellen eines Smarthosts für aktives Debuggen immens, da sie Implementierungen für viele Schnittstellen bereitstellt, die für Smarthosts benötigt werden.  
  
 Eine Hostanwendung muss nur drei Funktionen haben, um als Smart Host zu gelten, der einen `IDebugDocumentHelper` verwendet:  
  
1.  Führen Sie `CoCreate` für den prozessbasierten Debugmanager durch, und verwenden Sie die [IProcessDebugManager-Schnittstelle](../winscript/reference/iprocessdebugmanager-interface.md), um Ihre Anwendung der Liste von debugfähigen Anwendungen hinzuzufügen.  
  
2.  Erstellen Sie ein Hilfprogramm zum Debuggen eines Dokuments für alle Skriptobjekte über die [IProcessDebugManager::CreateDebugDocumentHelper](../winscript/reference/iprocessdebugmanager-createdebugdocumenthelper.md)-Methode. Stellen Sie sicher, dass der Dokumentname, das übergeordnete Dokument, der Text und die Skriptblöcke definiert sind.  
  
3.  Implementieren Sie die [IActiveScriptSiteDebug-Schnittstelle](../winscript/reference/iactivescriptsitedebug-interface.md) in Ihr Objekt, in das bereits die [IActiveScriptSite](../winscript/reference/iactivescriptsite.md)-Schnittstelle implementiert wurde (erforderlich für Active Scripting). Die einzige nicht triviale Methode für die `IActiveScriptSiteDebug`-Schnittstelle delegiert nur an das Hilfsprogramm.  
  
 Der Host kann optional die [IDebugDocumentHost-Schnittstelle](../winscript/reference/idebugdocumenthost-interface.md) implementieren, wenn er zusätzliche Kontrolle über die Syntaxfarbe, die Erstellung des Dokumentkontexts und andere erweiterte Funktionen benötigt.  
  
 Die größte Einschränkung des Smart Host-Hilfsprogramms ist, dass es nur Dokumente verarbeiten kann, deren Inhalte geändert oder verringert werden, nachdem sie hinzugefügt wurden (obwohl Dokumente auch erweitert werden können). Für die meisten Smart Hosts sind die Funktionen des Hilfsprogramms allerdings ausreichend.  
  
 In den folgenden Abschnitten wird jeder Schritt im Detail erläutert.  
  
## <a name="create-an-application-object"></a>Erstellen eines Anwendungsobjekts  
 Bevor das Smart Host-Hilfsprogramm verwendet wird, muss ein [IDebugApplication-Schnittstellenobjekt](../winscript/reference/idebugapplication-interface.md) erstellt werden, das Ihre Anwendung im Debugger darstellt.  
  
#### <a name="to-create-an-application-object"></a>Zum Erstellen einer Anwendungsseite müssen Sie:  
  
1.  Eine Instanz des prozessbasierten Debugmanager über eine `CoCreateInstance` erstellen.  
  
2.  [IProcessDebugManager::CreateApplication](../winscript/reference/iprocessdebugmanager-createapplication.md) aufrufen.  
  
3.  Den Namen für die Anwendung über [IDebugApplication::SetName](../winscript/reference/idebugapplication-setname.md) festlegen.  
  
4.  Das Anwendungsobjekt der Liste mit debugfähigen Anwendungen über [IProcessDebugManager::AddApplication](../winscript/reference/iprocessdebugmanager-addapplication.md) hinzufügen.  
  
     Im untenstehenden Code wird der Prozess dargestellt. Allerdings enthält er keine Techniken zum Prüfen von Fehlern oder andere stabile Programmierverfahren.  
  
    ```  
    CoCreateInstance(CLSID_ProcessDebugManager, NULL,  
          CLSCTX_INPROC_SERVER | CLSCTX_INPROC_HANDLER  
          | CLSCTX_LOCAL_SERVER,  
    IID_IProcessDebugManager, (void **)&g_ppdm);  
    g_ppdm->CreateApplication(&g_pda);  
    g_pda->SetName(L"My cool application");  
    g_ppdm->AddApplication(g_pda, &g_dwAppCookie);  
    ```  
  
## <a name="using-idebugdocumenthelper"></a>Verwenden von IDebugDocumentHelper  
  
#### <a name="to-use-the-helper-minimal-sequence-of-steps"></a>So verwenden Sie das Hilfsprogramm (minimale Schrittsequenz)  
  
1.  Erstellen Sie für jedes Hostdokument ein Hilfsprogramm über [IProcessDebugManager::CreateDebugDocumentHelper](../winscript/reference/iprocessdebugmanager-createdebugdocumenthelper.md).  
  
2.  Rufen Sie im Hilfsprogramm [IDebugDocumentHelper::Init](../winscript/reference/idebugdocumenthelper-init.md) auf, und spezifizieren Sie Name, Dokumentattribute usw.  
  
3.  Rufen Sie [IDebugDocumentHelper::Attach](../winscript/reference/idebugdocumenthelper-attach.md) (oder NULL, wenn er sich bei dem Dokument um den Stamm handelt) mit dem übergeordneten Hilfsprogramm für das Dokument auf, um die Position des Dokuments in der Struktur zu bestimmen, und machen Sie es sichtbar für den Debugger.  
  
4.  Rufen Sie [IDebugDocumentHelper::AddDBCSText](../winscript/reference/idebugdocumenthelper-adddbcstext.md) oder [IDebugDocumentHelper::AddUnicodeText](../winscript/reference/idebugdocumenthelper-addunicodetext.md), um den Text des Dokuments zu definieren. (Diese können mehrmals aufgerufen werden, wenn das Dokument, wie im Fall des Browsers, inkrementell herunterladen wird.)  
  
5.  Rufen Sie [IDebugDocumentHelper::DefineScriptBlock](../winscript/reference/idebugdocumenthelper-definescriptblock.md) auf, um die Geltungsbereiche der Skriptblöcke und die zugehörigen Skriptmodule zu definieren.  
  
## <a name="implementing-iactivescriptsitedebug"></a>Implementieren von IActiveScriptSiteDebug  
 Rufen Sie zum Implementieren von [IActiveScriptSiteDebug::GetDocumentContextFromPosition](../winscript/reference/iactivescriptsitedebug-getdocumentcontextfromposition.md) das der vorhanden Website zugehörige Hilfsprogramm auf, und rufen Sie anschließend wie folgt den Offset des Startdokuments für den vorhandenen Quellkontext auf:  
  
```  
pddh->GetScriptBlockInfo(dwSourceContext, NULL, &ulStartPos, NULL);  
```  
  
 Verwenden Sie dann das Hilfsprogramm, um einen neuen Dokumentkontext für den vorhandenen Zeichenoffset zu erstellen:  
  
```  
pddh->CreateDebugDocumentContext(ulStartPos + uCharacterOffset, cChars, &pddcNew);  
```  
  
 Rufen Sie nur `IDebugApplication::GetRootNode` (geerbt von [IRemoteDebugApplication::GetRootNode](../winscript/reference/iremotedebugapplication-getrootnode.md)) auf, um [IActiveScriptSiteDebug::GetRootApplicationNode](../winscript/reference/iactivescriptsitedebug-getrootapplicationnode.md) zu implementieren.  
  
 Geben Sie nur `IDebugApplication` zurück, die Sie anfänglich über den prozessbasierten Debugmanager erstellt haben, um [IDebugDocumentHelper::GetDebugApplicationNode](../winscript/reference/idebugdocumenthelper-getdebugapplicationnode.md) zu implementieren.  
  
## <a name="the-optional-idebugdocumenthost-interface"></a>Die optionale IDebugDocumentHost-Schnittstelle  
 Der Host kann eine Implementierung der [IDebugDocumentHost-Schnittstelle](../winscript/reference/idebugdocumenthost-interface.md) bereitstellen, wenn er [IDebugDocumentHelper::SetDebugDocumentHost](../winscript/reference/idebugdocumenthelper-setdebugdocumenthost.md) verwendet, um dieser zusätzliche Kontrolle über das Hilfsprogramm zu geben. Im Folgenden werden einige Schlüsselfunktionen dargestellt, die die Hostschnittstelle bereitstellt:  
  
-   Fügen Sie mithilfe von [IDebugDocumentHelper::AddDeferredText](../winscript/reference/idebugdocumenthelper-adddeferredtext.md) Text hinzu, damit der Host die tatsächlichen Zeichen nicht unmittelbar zur Verfügung stellen muss. Wenn die Zeichen tatsächlich benötigt werden, ruft das Hilfsprogramm [IDebugDocumentHost::GetDeferredText](../winscript/reference/idebugdocumenthost-getdeferredtext.md) für den Host auf.  
  
-   Setzen Sie die standardmäßig vom Hilfsprogramm zur Verfügung gestellten Syntaxfarben außer Kraft. Das Hilfsprogramm ruft [IDebugDocumentHost::GetScriptTextAttributes](../winscript/reference/idebugdocumenthost-getscripttextattributes.md) auf, um für einen bestimmten Zeichenbereich die Farben zu bestimmen. Dabei wird die Standardimplementierung wiederhergestellt, wenn der Host `E_NOTIMPL` zurückgibt.  
  
-   Stellen Sie eine unbekannte Steuerung für Dokumentenkontexte bereit, die über das Hilfsprogramm erstellt wurden, indem Sie [IDebugDocumentHost::OnCreateDocumentContext](../winscript/reference/idebugdocumenthost-oncreatedocumentcontext.md) implementieren. Dadurch kann der Host die Funktionen der standardmäßigen Implementierung des Dokumentenkontexts überschreiben.  
  
-   Stellen Sie im Dateisystem einen Pfadnamen für das Dokument zur Verfügung. Diese Funktion verwenden einige Benutzeroberflächen zum Debuggen, damit der Benutzer Änderungen an dem Dokument bearbeiten und speichern kann. [IDebugDocumentHost::NotifyChanged](../winscript/reference/idebugdocumenthost-notifychanged.md) wird aufgerufen, um den Host zu benachrichtigen, nachdem das Dokument gespeichert wurde.  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen mit Active Script – Übersicht](../winscript/active-script-debugging-overview.md)