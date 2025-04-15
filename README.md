# test___

```mermaid
graph TD
    A[UserManagement Initialized with username] --> B{Check if Admin}
    B -- Returns True --> C[Set is_admin = True]
    B -- Returns False --> D[Set is_admin = False]

    subgraph Button_Creation_in_init
        C --> E[Create Admin Buttons (Add, Del, View All, Viz)]
        E --> F[Create Common Buttons (Marks, ECA, Logout, Back)]
        D --> F
    end

    F --> G[Start run() Main Loop]

    subgraph Main_Loop_Event_Handling
        G --> H{is_admin True?}
        H -- Yes --> I[Check Clicks on Admin Buttons]
        I -- Add/Delete Click --> J[Show Add/Delete Form]
        I -- View/Viz Click --> K[Load Data, Show DataDisplayWindow]
        I -- No Admin Button Click --> L[Check Clicks on Common Buttons]
        H -- No --> L
        J --> G
        K --> G
        L -- View Click --> K
        L -- Logout/Back Click --> M[Quit to Main Menu (simple_ui)]
        L -- No Common Button Click --> G
    end

    subgraph Main_Loop_Drawing
        G --> N{is_admin True?}
        N -- Yes --> O[Draw Admin Buttons + Common Buttons]
        N -- No --> P[Draw Common Buttons Only]
        O --> G
        P --> G
    end
