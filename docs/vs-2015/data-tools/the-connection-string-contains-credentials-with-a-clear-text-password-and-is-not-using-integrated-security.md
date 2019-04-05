---
title: Die Verbindungszeichenfolge enthält Anmeldeinformationen mit einem Klartext-Kennwort und ist keine integrierten Sicherheit von | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 501d85af-92e0-4471-b280-8a59c0688575
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 02805bc9951c682c654b47ae49c15c7682bd60ee
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58956411"
---
# <a name="the-connection-string-contains-credentials-with-a-clear-text-password-and-is-not-using-integrated-security"></a>Die Verbindungszeichenfolge enthält Anmeldeinformationen mit einem Klartext-Kennwort und verwendet keine integrierte Sicherheit.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Möchten Sie die Verbindungszeichenfolge mit vertraulichen Informationen in der aktuellen DBML-Datei und in den Anwendungskonfigurationsdateien speichern?  Klicken Sie auf Nein, um die Verbindungszeichenfolge ohne die vertraulichen Informationen zu speichern.  
  
 Beim Arbeiten mit Datenverbindungen, die vertrauliche Informationen enthalten (in der Verbindungszeichenfolge enthaltene Kennwörter) haben Sie die Option, die Verbindungszeichenfolge mit den vertraulichen Informationen oder ohne diese in der DBML-Datei und der Anwendungskonfigurationsdatei des Projekts zu speichern.  
  
> [!WARNING]
>  Wenn Sie die Eigenschaft **Anwendungseinstellungen** der **Verbindungseigenschaften** auf **False** festlegen, wird das Kennwort der DBML-Datei hinzugefügt.  
  
### <a name="to-save-the-connection-string-with-the-sensitive-information-in-the-projects-application-settings"></a>So speichern Sie die Verbindungszeichenfolge mit den vertraulichen Informationen in den Anwendungseigenschaften des Projekts  
  
-   Klicken Sie auf **Ja**.  
  
     Die Verbindungszeichenfolge wird als Anwendungseinstellung gespeichert. Die Verbindungszeichenfolge enthält die vertraulichen Informationen als Klartext. Die vertraulichen Informationen sind nicht in der DBML-Datei enthalten.  
  
### <a name="to-save-the-connection-string-without-the-sensitive-information-in-the-projects-application-settings"></a>So speichern Sie die Verbindungszeichenfolge ohne die vertraulichen Informationen in den Anwendungseigenschaften des Projekts  
  
-   Klicken Sie auf **Nein**.  
  
     Die Verbindungszeichenfolge wird als Anwendungseinstellung gespeichert, jedoch ohne das Kennwort.  
  
## <a name="see-also"></a>Siehe auch  
 [LINQ to SQL-Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
