---
title: "Abfangen von Legacy-Dienst Sprachbefehle | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Befehle, Sprachdienst abfangen"
  - "Language Services Abfangen von Befehlen"
ms.assetid: eea69f03-349c-44bb-bd4f-4925c0dc3e55
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# Abfangen von Legacy-Dienst Sprachbefehle
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Mit [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]können Sie die Befehle Sprachendienst\-Abfang verfügen, die die Textansicht Andernfalls behandelt werden würde.  Dies ist für sprachspezifisches Verhalten nützlich, das die Textansicht unmanaged.  Sie können diese Befehle feststellen, indem Sie eine oder mehrere Filter auf die Textansicht des Befehls Sprachdienst hinzu.  
  
## Ruft den Befehl ab und weiterleitend  
 Ein Befehl ist ein Filter <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>\-Objekt, das bestimmte Zeichen oder sequenzen Befehle Schlüssel überwacht wird.  Sie können mehrere Filter mit einer einzelnen Befehls Textansicht zuordnen.  Jede Textansicht verwaltet einen Instanzenweg Filter.  Nachdem Sie einen neuen Befehl Filter erstellen, fügen Sie den Filter der Kette für die entsprechende Textansicht.  
  
 Rufen Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>\-Methode auf <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> Befehls auf, um den Filter hinzuzufügen der Kette.  Wenn Sie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>aufrufen, gibt [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Befehls einen anderen Filter zurück, an dem Sie die Befehle übergeben können, die der Filter Befehl nicht behandelt.  
  
 Sie haben folgende Möglichkeiten für die Behandlung:  
  
-   Behandeln Sie den Befehl und leiten Sie dann den folgenden Befehl an den Befehl Filter in der Kette weiter.  
  
-   Behandeln Sie den Befehl und leiten Sie den Befehl keine Verbindung mit dem Filter folgenden Befehls.  
  
-   Behandeln Sie nicht den Befehl auszuführen, aber Sie den Befehl an den Filter folgenden Befehls.  
  
-   Ignoriert den Befehl.  Behandeln Sie es nicht im aktuellen Filter, und geben Sie es nicht an den nächsten Filter weitergeleitet.  
  
 Informationen dazu, welche Befehle der Sprachdienst behandeln sollte, finden Sie unter [Wichtige Befehle für Language Service\-Filter](../../extensibility/internals/important-commands-for-language-service-filters.md).