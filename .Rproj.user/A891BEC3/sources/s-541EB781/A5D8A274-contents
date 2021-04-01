function(input, output) {
    
    
    reactive_employee <- reactive({
        
        data_attrition %>% 
            filter(attrition == input$status) #ini sama dengan id radio button yang ada di UI
        
    })
    
    output$job_sat <- renderValueBox({
        
        value_job_satisfaction <- reactive_employee() %>% 
            pull(job_satisfaction) %>% 
            mean() %>% 
            round(2)
        
        valueBox(
            value = value_job_satisfaction, 
            subtitle = "Avg Job Satisfaction",
            icon = icon("smile"),
            color = "green", width = 3
        )
    })
    
    output$env_sat <- renderValueBox({
        
        
        value_env_satisfaction <- reactive_employee() %>% #object reactive di tandai dengan tanda kurung
            pull(environment_satisfaction) %>% #pull ini ambil vector nilai nya , select masih berupa data frame
            mean() %>% 
            round(2)
        
        valueBox(
            value = value_env_satisfaction, 
            subtitle = "Avg Environment Satisfaction",
            icon = icon("user-friends"),
            color = "green", width = 3
        )
        
    })
    
    output$tenure <- renderValueBox({
        
        avg_tenure_inactive <- reactive_employee() %>% 
            pull(years_at_company) %>% 
            mean() %>% 
            round(2) * 12
        
        valueBox(
            value = paste(avg_tenure_inactive, "Months"), #menampilkan angka + string
            subtitle = "Avg tenure of employees",
            icon = icon("spinner"),
            color = "green",
            width = 3
        )
        
    })
    
    
    output$income <- renderValueBox({
        
        avg_income <- reactive_employee() %>% 
            pull(monthly_income) %>% 
            mean() %>% 
            round(2) %>% 
            dollar()
        
        valueBox(
            value = avg_income,
            subtitle = "Avg monthly income",
            icon = icon("comment-dollar"),
            color = "red",
            width = 3
        )
    })
    
    ### ini untuk golah data plot
    
    output$personalNum <- renderPlotly({
        
        title_num <- input$pers_num %>%
            str_replace_all(pattern = "_", replacement = " ") %>%
            str_to_title()
        
        p <- ggplot(data_attrition, aes_string(input$pers_num)) +
            geom_density(aes(fill = attrition), alpha = 0.7) +
            scale_fill_manual(values = c("firebrick", "dodgerblue4")) +
            labs(
                title = title_num,
                x = NULL,
                fill = "Attrition"
            ) +
            theme_bw()
        
        ggplotly(p)
        
    })
    
    
}
