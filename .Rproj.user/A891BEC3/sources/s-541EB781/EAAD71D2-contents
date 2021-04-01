dashboardPage(
    skin = "black",
    dashboardHeader(title = "Newton IP"),
    dashboardSidebar(
        sidebarMenu(
            menuItem(
                text = "Personal",
                tabName = "personal",#ini adalah "id" dari menu item
                icon = icon("gears")
            ),
            menuItem(
                text = "Billing",
                tabName = "billing",#ini adalah "id" dari menu item
                icon = icon("tasks")
            ),
            menuItem(
                text = "Work",
                tabName = "work",#ini adalah "id" dari menu item
                icon = icon("cubes")
            ),
            menuItem(
                text = "Profile",
                tabName = "profile",#ini adalah "id" dari menu item )cari di fontowesome
                icon = icon("chart-area")
            )
        )
    ),
    dashboardBody(
        tabItems(
            tabItem(
                tabName = "personal",#ini sesuai dengan nama id yg menu item di atas
                
                fluidRow(
                    # box(
                    #    title = "Overview",
                    #    width = 12,
                    #    
                    #    valueBox(
                    #        value = max(iris$Sepal.Length), 
                    #        subtitle = "contoh",
                    #        icon = icon("chart-area"),
                    #        color = "green",
                    #        width = 4
                    #    ),
                    #    valueBox(
                    #        value = 20, 
                    #        subtitle = "contoh",
                    #        icon = icon("chart-area"),
                    #        color = "red",
                    #        width = 4
                    #    ),
                    #    valueBox(
                    #        value = 15, 
                    #        subtitle = "contoh",
                    #        icon = icon("chart-area"),
                    #        color = "orange",
                    #        width = 4
                    #    )
                    # )
                    
                    box(
                        title = "Overview",
                        width = 12, 
                        
                        radioButtons(inputId = "status", 
                                     label = "Attrition status?", 
                                     choices = unique(data_attrition$attrition), #pengganti unique bisa c("yes","no")
                                     inline = TRUE), #inline true supaya kesamping
                        
                        valueBoxOutput(
                            outputId = "job_sat", width = 3 #valueboxoutput ini di control sama respon user
                        ),
                        
                        valueBoxOutput(
                            outputId = "env_sat", width = 3 
                        ),
                        
                        valueBoxOutput(
                            outputId = "tenure", width = 3 
                        ),
                        
                        valueBoxOutput(
                            outputId = "income", width = 3 
                        )
                    )
                ),
                
                fluidRow(
                    box(
                        title = "Numerical variable",
                        width = 12,
                        
                        selectInput(
                            inputId = "pers_num",
                            label = "Pilih variabel numerik yang ingin diamati",
                            choices = data_attrition %>% 
                                select(age, distance_from_home, 
                                       total_working_years, 
                                       num_companies_worked) %>% 
                                colnames(),
                            selected = "distance_from_home" #pilihan pertama ketika running
                        ),
                        
                        plotlyOutput(outputId = "personalNum")
                    )
                )
            )
        )
    )
)