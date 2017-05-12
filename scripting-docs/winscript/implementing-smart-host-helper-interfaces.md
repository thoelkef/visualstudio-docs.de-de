---
title: "Implementieren von Smart Host-Hilfsprogrammschnittstellen | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Smarthost-Hilfsprogrammschnittstellen, Implementieren"
ms.assetid: b9c44246-4d4d-469e-91be-00c8f5796fa5
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Implementieren von Smart Host-Hilfsprogrammschnittstellen
Die [IDebugDocumentHelper\-Schnittstelle](../winscript/reference/idebugdocumenthelper-interface.md)\-Schnittstelle groß vereinfacht das Erstellen eines Smarthosts für aktives Debuggen, da sie Implementierungen für viele Schnittstellen bereitstellt, die für intelligente Hosting erforderlich sind.  
  
 Um ein Smarthost zu sein, der `IDebugDocumentHelper` verwendet, muss eine Hostanwendung nur drei Schritte ausführen:  
  
1.  `CoCreate` der Prozessdebug\-Manager und verwenden die [IProcessDebugManager\-Schnittstelle](../winscript/reference/iprocessdebugmanager-interface.md)\-Schnittstelle, um die Anwendung der Liste der debugfähigen Anwendungen hinzuzufügen.  
  
2.  Erstellen Sie eine Debug\- Dokumentenhilfe für jedes Skriptobjekt, mithilfe der [IProcessDebugManager::CreateDebugDocumentHelper](../winscript/reference/iprocessdebugmanager-createdebugdocumenthelper.md)\-Methode.  Stellen Sie sicher, dass der Dokumentname, das Dokument des übergeordneten Elements, der Text und die Skriptblöcke definiert werden.  
  
3.  Implementieren Sie die [IActiveScriptSiteDebug\-Schnittstelle](../winscript/reference/iactivescriptsitedebug-interface.md)\-Schnittstelle für das Objekt, das die [IActiveScriptSite](../winscript/reference/iactivescriptsite.md)\-Schnittstelle implementiert \(die für Active Scripting erforderlich ist\).  Die einzige nicht\-triviale Methode auf den Delegaten `IActiveScriptSiteDebug`\-Schnittstelle einfach zur Verfügung.  
  
 Optional kann der Host die [IDebugDocumentHost\-Schnittstelle](../winscript/reference/idebugdocumenthost-interface.md)\-Schnittstelle implementieren, wenn er zusätzliche Kontrolle über Syntaxfarbe, Dokumentenkontexterstellung und anderer erweiterter Funktionen erfordert.  
  
 Die Haupteinschränkung für die Smarthosthilfe ist, dass sie nur Dokumente bearbeiten kann, deren Inhalt oder Verkleinerung ändert, nachdem sie hinzugefügt wurden \(obwohl Dokumente erweitern können.\)  Für viele Smarthosts ist jedoch die Funktionen, die bereitstellt, genau, was benötigt wird.  
  
 In den folgenden Abschnitten werden die einzelnen Schritte ausführlicher beschrieben.  
  
## Erstellen Sie ein Anwendungsobjekt  
 Bevor die Smarthosthilfe verwendet werden kann, ist es notwendig, [IDebugApplication\-Schnittstelle](../winscript/reference/idebugapplication-interface.md) ein Objekt zu erstellen, um die Anwendung im Debugger darzustellen.  
  
#### So fügen Sie ein Anwendungsobjekt erstellen  
  
1.  Erstellen Sie eine Instanz des Debug\- ProzessManagers, der `CoCreateInstance` verwendet.  
  
2.  Rufen Sie [IProcessDebugManager::CreateApplication](../winscript/reference/iprocessdebugmanager-createapplication.md) auf.  
  
3.  Legen Sie den Namen der Anwendung fest, indem Sie [IDebugApplication::SetName](../winscript/reference/idebugapplication-setname.md) haben.  
  
4.  Fügen Sie das Anwendungsobjekt zur Liste der debugfähigen Anwendungen hinzu, indem Sie [IProcessDebugManager::AddApplication](../winscript/reference/iprocessdebugmanager-addapplication.md) verwenden.  
  
     Im folgenden Code wird das Verfahren, aber er enthält keine Fehlerprüfung oder andere stabile Programmiermethoden.  
  
    ```  
    CoCreateInstance(CLSID_ProcessDebugManager, NULL,  
          CLSCTX_INPROC_SERVER | CLSCTX_INPROC_HANDLER  
          | CLSCTX_LOCAL_SERVER,  
    IID_IProcessDebugManager, (void **)&g_ppdm);  
    g_ppdm->CreateApplication(&g_pda);  
    g_pda->SetName(L"My cool application");  
    g_ppdm->AddApplication(g_pda, &g_dwAppCookie);  
    ```  
  
## Verwenden IDebugDocumentHelper  
  
#### Um die Hilfe \(minimale Schrittfolge\) verwenden  
  
1.  Für jedes Hostdokument erstellen Sie eine Hilfe erstellt, die [IProcessDebugManager::CreateDebugDocumentHelper](../winscript/reference/iprocessdebugmanager-createdebugdocumenthelper.md) verwendet.  
  
2.  Rufen Sie [IDebugDocumentHelper::Init](../winscript/reference/idebugdocumenthelper-init.md) auf der Hilfe an und den Namen geben, Dokumentenattribute, u. a.  
  
3.  Rufen Sie [IDebugDocumentHelper::Attach](../winscript/reference/idebugdocumenthelper-attach.md) mit übergeordneter Hilfe für das Dokument \(oder MAKE ungültig, wenn das Dokument der Stamm ist\), um die Position des Dokuments in der Struktur zu definieren und sie sichtbar zu machen an den Debugger.  
  
4.  Rufen Sie [IDebugDocumentHelper::AddDBCSText](../winscript/reference/idebugdocumenthelper-adddbcstext.md) oder [IDebugDocumentHelper::AddUnicodeText](../winscript/reference/idebugdocumenthelper-addunicodetext.md) an, um den Text des Dokuments zu definieren.  \(Diese können mehrmals aufgerufen werden, wenn Dokument inkrementell heruntergeladen wird, wie im Fall eines Browsers.\)  
  
5.  Rufen Sie [IDebugDocumentHelper::DefineScriptBlock](../winscript/reference/idebugdocumenthelper-definescriptblock.md) an, um die Bereiche für jeden Skriptblock und die zugeordneten Skriptmodule zu definieren.  
  
## Implementieren von IActiveScriptSiteDebug  
 Um [IActiveScriptSiteDebug::GetDocumentContextFromPosition](../winscript/reference/iactivescriptsitedebug-getdocumentcontextfromposition.md) zu implementieren, rufen Sie die Hilfe entsprechend der angegebenen Site ab, und rufen Sie anschließend das beginnen Dokument ab, das für den angegebenen Quellkontext versetzt ist, wie folgt:  
  
```  
pddh->GetScriptBlockInfo(dwSourceContext, NULL, &ulStartPos, NULL);  
```  
  
 Als Nächstes verwenden Sie die Hilfe, um einen Kontext des neuen Dokuments für das angegebene ausgeglichene Zeichen zu erstellen:  
  
```  
pddh->CreateDebugDocumentContext(ulStartPos + uCharacterOffset, cChars, &pddcNew);  
```  
  
 Um [IActiveScriptSiteDebug::GetRootApplicationNode](../winscript/reference/iactivescriptsitedebug-getrootapplicationnode.md) zu implementieren, rufen Sie einfach `IDebugApplication::GetRootNode` an \(geerbt von [IRemoteDebugApplication::GetRootNode](../winscript/reference/iremotedebugapplication-getrootnode.md)\).  
  
 Um [IDebugDocumentHelper::GetDebugApplicationNode](../winscript/reference/idebugdocumenthelper-getdebugapplicationnode.md) zu implementieren, geben Sie lediglich `IDebugApplication` zurück, das Sie zuerst mit dem Debuggen ProzessManagers erstellt haben.  
  
## Die optionale IDebugDocumentHost\-Schnittstelle  
 Der Host kann eine Implementierung [IDebugDocumentHost\-Schnittstelle](../winscript/reference/idebugdocumenthost-interface.md) mit [IDebugDocumentHelper::SetDebugDocumentHost](../winscript/reference/idebugdocumenthelper-setdebugdocumenthost.md) bereitstellen, um ihr zusätzliche Steuerungsmöglichkeiten über die Hilfe zu geben.  Im Folgenden einige der Schlüsselsachen, die die Hostschnittstelle ermöglicht, eine:  
  
-   Fügen Sie Text mithilfe [IDebugDocumentHelper::AddDeferredText](../winscript/reference/idebugdocumenthelper-adddeferredtext.md) hinzu, sodass der Host ist nicht erforderlich, um die tatsächlichen Zeichen sofort bereitzustellen.  Wenn die Zeichen tatsächlich benötigt werden, ruft die Hilfe [IDebugDocumentHost::GetDeferredText](../winscript/reference/idebugdocumenthost-getdeferredtext.md) auf dem Host an.  
  
-   Überschreiben Sie die standardmäßige Syntaxfarbe, die von der Hilfe bereitgestellt wird.  Die Hilfe [IDebugDocumentHost::GetScriptTextAttributes](../winscript/reference/idebugdocumenthost-getscripttextattributes.md) ruft auf, um den Farbton für einen Bereich von Zeichen, das Fallen zu bestimmen hinter auf seiner Standardimplementierung wenn die Hostrückgabe `E_NOTIMPL`.  
  
-   Erstellen Sie ein steuerndes unbekannt für die Dokumentenkontexte zur Verfügung, die von der Hilfe erstellt werden, indem Sie [IDebugDocumentHost::OnCreateDocumentContext](../winscript/reference/idebugdocumenthost-oncreatedocumentcontext.md) implementieren.  Dies ermöglicht es dem Host, die Funktionen der Standard Dokumentenkontextimplementierung zu überschreiben.  
  
-   Geben Sie einen Pfadnamen im Dateisystem des Dokuments angezeigt.  Einige debuggende UIs\-Verwendung dieses, den Benutzer zu ermöglichen, Änderungen am Dokument zu bearbeiten und zu speichern.  [IDebugDocumentHost::NotifyChanged](../winscript/reference/idebugdocumenthost-notifychanged.md) wird aufgerufen, um den Host zu benachrichtigen, nachdem das Dokument gespeichert wurde.  
  
## Siehe auch  
 [Debuggen mit Active Script \- Übersicht](../winscript/active-script-debugging-overview.md)