---
title: "Gewusst wie: Migrieren von Erweiterungsprojekte in Visual Studio 2015 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Visual Studio SDK aktualisieren"
ms.assetid: 22491cdc-8f04-4e1c-8eb4-ff33798ec792
caps.latest.revision: 25
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 25
---
# Gewusst wie: Migrieren von Erweiterungsprojekte in Visual Studio 2015
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Hier ist die Erweiterung zu aktualisieren.  
  
> [!IMPORTANT]
>  Wenn Sie eine Version der Erweiterung Lösung für eine frühere Version von Visual Studio verwalten möchten, sollten Sie unbedingt eine Kopie zu erstellen, bevor Sie aktualisieren. Es möglicherweise schwierig, die aktualisierte Version in den vorherigen Zustand zurück.  
  
#### So aktualisieren Sie eine Projektmappe Erweiterbarkeit  
  
1.  Mithilfe der Kopie soll aktualisieren, sie in der neuen Version öffnen. Sie werden aufgefordert, das Upgrade nicht rückgängig gemacht werden.  
  
2.  Nachdem das Upgrade abgeschlossen ist, ändern Sie den Pfad des externen Programms auf die neue Version von devenv.exe. Mit der rechten Maustaste des Projektknoten in der **Projektmappen\-Explorer**, wählen Sie dann **Eigenschaften**. In der **Debuggen** Registerkarte, finden Sie im Textfeld durch **externes Programm starten** und ändern Sie den Pfad von devenv.exe in der Visual Studio 2015\-Pfad, die etwa wie folgt aussieht:  
  
     **%ProgramFiles%\\Microsoft visual Studio 14.0\\Common7\\IDE\\devenv.exe**  
  
3.  Fügen Sie einen Verweis auf Microsoft.VisualStudio.Shell.14.0.dll hinzu. \(Mit der rechten Maustaste des Projektknoten in der **Projektmappen\-Explorer** und wählen Sie dann **Hinzufügen \/ Reference**. Wählen Sie die **Extensions** Registerkarte, und überprüfen Sie dann **Microsoft.VisualStudio.Shell.14.0**.\)  
  
4.  Erstellen Sie die Projektmappe. Die erstellten Dateien sind, bereitgestellt:  
  
     **%LOCALAPPDATA%\\Microsoft\\VisualStudio.14.0Exp\\Extensions\\ \< Name des Autors \> \\ \< Projektname \> \\ \< Projektversion \> \\**.  
  
#### Aktualisieren Sie ein Erweiterungsprojekt, NuGet Visual Studio SDK\-Verweisassemblys  
  
1.  Bestimmen Sie die Visual Studio SDK\-Verweisassemblys, die das Projekt benötigt.  In **Projektmappen\-Explorer**, erweitern Sie das Projekt **Verweise** Knoten, und überprüfen Sie die Liste der Verweise.  Visual Studio SDK verweisen auf Assemblys haben das Präfix **Microsoft.VisualStudio** im Namen \(z. B.: Microsoft.VisualStudio.Shell.14.0\).  
  
2.  Die Visual Studio SDK\-Verweisassemblys aus dem Projekt entfernen, indem Sie sie auswählen, klicken Sie mit der rechten Maustaste auf und **Entfernen**.  
  
3.  Fügen Sie die NuGet\-Versionen von Visual Studio SDK\-Verweisassemblys.  In der die **Projektmappen\-Explorer Verweise** Knoten, öffnen Sie die **NuGet\-Pakete verwalten...** Dialogfeld.  Weitere Informationen zu diesem Dialogfeld finden Sie unter [Verwalten von NuGet\-Paketen mithilfe des Dialogs](http://docs.nuget.org/Consume/Package-Manager-Dialog). Die Visual Studio SDK\-Verweisassemblys werden veröffentlicht, auf ["NuGet.org"](http://www.nuget.org) von [VisualStudioExtensibility](http://www.nuget.org/profiles/VisualStudioExtensibility).  
  
4.  Mithilfe von **nuget.org** als Ihre **Paketquelle**, Suche nach dem Namen des NuGet\-Paket das gewünschte Verweisassembly entspricht \(zum Beispiel: Microsoft.VisualStudio.Shell.14.0\) und installieren Sie es in Ihrem Projekt.  NuGet kann mehrere Verweisassemblys hinzufügen, um die ursprüngliche Assembly Abhängigkeiten zu erfüllen.  
  
     Falls gewünscht, können Sie die Visual Studio SDK\-Verweisassemblys gleichzeitig hinzufügen, indem Sie das Visual Studio SDK installieren [Meta\-Paket](http://www.nuget.org/packages/VSSDK_Reference_Assemblies).  
  
5.  Sie können auch auf die NuGet\-Version von Visual Studio SDK Build\-Tools wechseln. Dieses NuGet\-Paket ist [Microsoft.VSSDK.BuildTools](http://www.nuget.org/packages/Microsoft.VSSDK.BuildTools) und einmal hinzugefügt, um Ihr Projekt umfasst die erforderlichen Tools und Dateien Erweiterbarkeitsprojekt auf einem Computer ohne Installation des Visual Studio SDK erstellen zu können.  
  
> [!NOTE]
>  Es ist nicht erforderlich, dass Sie Ihre vorhandenen Erweiterungsprojekte Verwendung von NuGet\-Verweisassemblys und Tools aktualisieren.  Sie können weiterhin erstellen Sie mithilfe von Verweisassemblys und Tools, die mit dem Visual Studio\-SDK installiert.