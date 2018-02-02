---
title: Demo-Beispiel | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- demo sample [Visual Studio ALM]
- code analysis, samples
ms.assetid: 09e1b9f7-5916-4ed6-a001-5c2d7e710682
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: be42ed54e2c245a47e885fe8310c106c27ea82b2
ms.sourcegitcommit: d6327b978661c0a745bf4b59f32d8171607803a3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2018
---
# <a name="demo-sample"></a>Demobeispiel
Dieses Verfahren veranschaulichen das Erstellen des Beispiels für [Exemplarische Vorgehensweise: Analysieren von C/C++-Code für Mängel](../code-quality/walkthrough-analyzing-c-cpp-code-for-defects.md). Die Prozeduren erstellen:  
  
-   Ein [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Projektmappe mit dem Namen CppDemo.  
  
-   Ein statisches Bibliotheksprojekt mit dem Namen CodeDefects aus.  
  
-   Ein statisches Bibliotheksprojekt mit dem Namen Anmerkungen.  
  
 Die Prozeduren bieten auch den Code für die Header und CPP-Dateien für den statischen Bibliotheken.  
  
### <a name="create-the-cppdemo-solution-and-the-codedefects-project"></a>Erstellen der CppDemo-Projektmappe und das Projekt CodeDefects  
  
1.  Klicken Sie auf die **Datei** Sie im Menü **neu**, und klicken Sie dann auf **neues Projekt**.  
  
2.  In der **-Projekttypen** Struktur Liste, erweitern Sie bei Visual C++ nicht als Standardsprache in VS ist **andere Sprachen**.  
  
3.  Erweitern Sie **Visual C++**, und klicken Sie dann auf **allgemeine**.  
  
4.  In **Vorlagen**, klicken Sie auf **leeres Projekt**.  
  
5.  In der **Namen** Textfeld **CodeDefects**.  
  
6.  Wählen Sie die **Projektmappenverzeichnis erstellen** Kontrollkästchen.  
  
7.  In der **Projektmappenname** Textfeld **CppDemo**.  
  
### <a name="configure-the-codedefects-project-as-a-static-library"></a>Konfigurieren Sie das Projekt CodeDefects als statische Bibliothek  
  
1.  Klicken Sie im Projektmappen-Explorer mit der Maustaste **CodeDefects** , und klicken Sie dann auf **Eigenschaften**.  
  
2.  Erweitern Sie **Konfigurationseigenschaften** , und klicken Sie dann auf **allgemeine**.  
  
3.  In der **allgemeine** Liste, wählen Sie den Text in der Spalte neben **Zielerweiterung**, und geben Sie dann **lib**.  
  
4.  In **Projektstandards**, klicken Sie auf die Spalte neben **Konfigurationstyp**, und klicken Sie dann auf **statische Bibliothek (.lib)**.  
  
### <a name="add-the-header-and-source-file-to-the-codedefects-project"></a>Fügen Sie die Header- und Quelle-Datei zum CodeDefects-Projekt  
  
1.  Erweitern Sie im Projektmappen-Explorer **CodeDefects**, mit der rechten Maustaste **Headerdateien**, klicken Sie auf **hinzufügen**, und klicken Sie dann auf **neues Element**.  
  
2.  In der **neues Element hinzufügen** (Dialogfeld), klicken Sie auf **Code**, und klicken Sie dann auf **Headerdatei (. h)**.  
  
3.  In der **Namen** geben **Bug.cpp** , und klicken Sie dann auf **hinzufügen**.  
  
4.  Kopieren Sie den folgenden Code, und fügen Sie ihn in die **Bug.cpp** in der Datei die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Editor.  
  
    ```cpp
    #include <windows.h>  
  
    //    
    //These 3 functions are consumed by the sample  
    //  but are not defined. This project cannot be linked!  
    //  
  
    bool CheckDomain( LPCSTR );  
    HRESULT ReadUserAccount();  
  
    //  
    //These constants define the common sizes of the   
    //  user account information throughout the program  
    //  
  
    const int USER_ACCOUNT_LEN = 256;  
    const int ACCOUNT_DOMAIN_LEN = 128;  
    ```  
  
5.  Klicken Sie im Projektmappen-Explorer mit der Maustaste **Quelldateien**, zeigen Sie auf **neu**, und klicken Sie dann auf **neues Element**.  
  
6.  In der **neues Element hinzufügen** (Dialogfeld), klicken Sie auf **C++-Datei (.cpp)**  
  
7.  In der **Namen** geben **Bug.cpp** , und klicken Sie dann auf **hinzufügen**.  
  
8.  Kopieren Sie den folgenden Code, und fügen Sie ihn in die Datei "Bug.h" in der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Editor.  
  
    ```cpp
    #include <stdlib.h>  
    #include "Bug.h"  
  
    // the user account   
    TCHAR g_userAccount[USER_ACCOUNT_LEN] = "";  
    int len = 0;  
  
    bool ProcessDomain()  
    {  
        TCHAR* domain = new TCHAR[ACCOUNT_DOMAIN_LEN];  
        // ReadUserAccount gets a 'domain\user' input from   
        //the user into the global 'g_userAccount'  
        if (ReadUserAccount() )  
        {  
  
            // Copies part of the string prior to the '\'   
            // character onto the 'domain' buffer  
            for( len = 0 ; (len < ACCOUNT_DOMAIN_LEN) && (g_userAccount[len] != '\0') ; len++  )  
            {  
                if ( g_userAccount[len] == '\\' )   
                {  
                    // Stops copying on the domain and user separator ('\')   
                    break;  
                }  
                domain[len] = g_userAccount[len];          
            }  
            if((len= ACCOUNT_DOMAIN_LEN) || (g_userAccount[len] != '\\'))  
            {  
                // '\' was not found. Invalid domain\user string.  
                delete [] domain;  
                return false;  
            }  
            else  
            {  
                domain[len]='\0';  
            }  
            // Process domain string  
            bool result = CheckDomain( domain );  
  
            delete[] domain;  
            return result;  
        }  
        return false;  
    }  
  
    int path_dependent(int n)  
    {  
        int i;  
        int j;  
        if (n == 0)  
            i = 1;  
        else  
            j = 1;  
        return i+j;   
    }  
    ```  
  
9. Klicken Sie auf die **Datei** Menü, und klicken Sie dann auf **alle speichern**.  
  
### <a name="add-the-annotations-project-and-configure-it-as-a-static-library"></a>Fügen Sie die Anmerkungen-Projekt hinzu und konfiguriert ihn als eine statische Bibliothek  
  
1.  Klicken Sie im Projektmappen-Explorer auf **CppDemo**, zeigen Sie auf **hinzufügen**, und klicken Sie dann auf **neues Projekt**.  
  
2.  In der **neues Projekt hinzufügen** Dialogfeld Feld, erweitern Sie die Visual C++, klicken Sie auf **allgemeine**, und klicken Sie dann auf **leeres Projekt**.  
  
3.  In der **Namen** Textfeld **Anmerkungen**, und klicken Sie dann auf **hinzufügen**.  
  
4.  Klicken Sie im Projektmappen-Explorer mit der Maustaste **Anmerkungen** , und klicken Sie dann auf **Eigenschaften**.  
  
5.  Erweitern Sie **Konfigurationseigenschaften** , und klicken Sie dann auf **allgemeine**.  
  
6.  In der **allgemeine** Liste, wählen Sie den Text in der Spalte neben **Zielerweiterung**, und geben Sie dann **lib**.  
  
7.  In **Projektstandards**, klicken Sie auf die Spalte neben **Konfigurationstyp**, und klicken Sie dann auf **statische Bibliothek (.lib)**.  
  
### <a name="add-the-header-file-and-source-file-to-the-annotations-project"></a>Hinzufügen der Headerdatei und der Quelldatei zum Annotations-Projekt  
  
1.  Erweitern Sie im Projektmappen-Explorer **Anmerkungen**, mit der rechten Maustaste **Headerdateien**, klicken Sie auf **hinzufügen**, und klicken Sie dann auf **neues Element**.  
  
2.  In der **neues Element hinzufügen** (Dialogfeld), klicken Sie auf **Headerdatei (. h)**.  
  
3.  In der **Namen** geben **annotations.h** , und klicken Sie dann auf **hinzufügen**.  
  
4.  Kopieren Sie den folgenden Code, und fügen Sie ihn in die **annotations.h** in der Datei die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Editor.  
  
    ```cpp
    #include <CodeAnalysis/SourceAnnotations.h>  
  
    struct LinkedList  
    {  
        struct LinkedList* next;  
        int data;  
    };  
  
    typedef struct LinkedList LinkedList;  
  
    [returnvalue:SA_Post( Null=SA_Maybe )] LinkedList* AllocateNode();  
  
    ```  
  
5.  Klicken Sie im Projektmappen-Explorer mit der Maustaste **Quelldateien**, zeigen Sie auf **neu**, und klicken Sie dann auf **neues Element**.  
  
6.  In der **neues Element hinzufügen** (Dialogfeld), klicken Sie auf **Code** , und klicken Sie dann auf **C++-Datei (.cpp)**  
  
7.  In der **Namen** geben **annotations.cpp** , und klicken Sie dann auf **hinzufügen**.  
  
8.  Kopieren Sie den folgenden Code, und fügen Sie ihn in die **annotations.cpp** in der Datei die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Editor.  
  
    ```cpp
    #include <CodeAnalysis/SourceAnnotations.h>  
    #include <windows.h>  
    #include <stdlib.h>    
    #include "annotations.h"  
  
    LinkedList* AddTail( LinkedList *node, int value )  
    {  
        LinkedList *newNode = NULL;   
  
        // finds the last node  
        while ( node->next != NULL )   
        {  
            node = node->next;  
        }  
  
        // appends the new node  
        newNode = AllocateNode();   
        newNode->data = value;  
        newNode->next = 0;  
        node->next = newNode;  
  
        return newNode;  
    }  
  
    ```  
  
9. Klicken Sie auf die **Datei** Menü, und klicken Sie dann auf **alle speichern**.