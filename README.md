# chat
this is a simple AI employee chatbot
import streamlit as st
import re

# Define the chatbot response function
def chatbot_response(user_input):
    responses = {
        r'work hours|working hours|office hours': 'Our standard work hours are from 9 AM to 5 PM, Monday to Friday.',
        r'leave policy|vacation days|time off|sick leave': 'Employees are entitled to 20 days of paid leave per year. Sick leave is provided as per the statutory guidelines.',
        r'health insurance|medical coverage|insurance|benefits': 'We provide comprehensive health insurance that covers medical, dental, and vision care.',
        r'remote work|working remotely|telecommuting|work from home': 'Remote work is allowed with manager approval and based on company policy.',
        r'salary|pay|compensation|wages': 'Salaries are paid bi-weekly, and we conduct annual reviews to discuss salary adjustments.',
        r'benefits|employee benefits|perks|allowances': 'Our benefits package includes health insurance, retirement plans, and employee discounts. We also provide allowances for work-related expenses.',
        r'training|professional development|skill development|education': 'We offer various training programs to help employees develop their skills and advance their careers. Educational support is also available.',
        r'promotion|advancement|career growth|raise': 'Promotions are based on performance, tenure, and company needs. We conduct reviews annually and consider raises during this process.',
        r'performance review|performance evaluation|appraisal': 'Performance reviews are conducted annually to assess employee performance and set goals for the upcoming year.',
        r'termination|resignation|dismissal|firing': 'Termination procedures are in accordance with company policy and legal regulations. Employees are given notice as per their contract and local laws.',
        r'work-from-home equipment|home office setup|equipment policy': 'The company provides essential equipment for remote work upon request and approval. Employees are responsible for maintaining their home office setup.',
        r'travel policy|business trips|travel expenses': 'Business travel is subject to approval and reimbursement of expenses as per company policy. Travel guidelines are provided before each trip.',
        r'workplace safety|safety procedures|health and safety': 'We prioritize workplace safety and follow strict health and safety procedures. Regular training is provided to ensure compliance with safety standards.',
        r'equal opportunity|diversity and inclusion|non-discrimination': 'We are committed to providing equal employment opportunities and fostering a diverse and inclusive work environment.',
        r'flexible working hours|flex-time|work schedule': 'Flexible working hours are available with manager approval. Employees can request adjustments to their work schedule as needed.'
    }
    
    user_input = user_input.lower()
    for pattern, response in responses.items():
        if re.search(pattern, user_input):
            return response
    
    return 'Sorry, I did not understand that.'

# Streamlit app
def main():
    st.title("HR Policy Chatbot")

    # Display the chatbot code
    st.subheader("Chatbot Code")
    code = """
import re

def chatbot_response(user_input):
    responses = {
        r'work hours|working hours|office hours': 'Our standard work hours are from 9 AM to 5 PM, Monday to Friday.',
        r'leave policy|vacation days|time off|sick leave': 'Employees are entitled to 20 days of paid leave per year. Sick leave is provided as per the statutory guidelines.',
        r'health insurance|medical coverage|insurance|benefits': 'We provide comprehensive health insurance that covers medical, dental, and vision care.',
        r'remote work|working remotely|telecommuting|work from home': 'Remote work is allowed with manager approval and based on company policy.',
        r'salary|pay|compensation|wages': 'Salaries are paid bi-weekly, and we conduct annual reviews to discuss salary adjustments.',
        r'benefits|employee benefits|perks|allowances': 'Our benefits package includes health insurance, retirement plans, and employee discounts. We also provide allowances for work-related expenses.',
        r'training|professional development|skill development|education': 'We offer various training programs to help employees develop their skills and advance their careers. Educational support is also available.',
        r'promotion|advancement|career growth|raise': 'Promotions are based on performance, tenure, and company needs. We conduct reviews annually and consider raises during this process.',
        r'performance review|performance evaluation|appraisal': 'Performance reviews are conducted annually to assess employee performance and set goals for the upcoming year.',
        r'termination|resignation|dismissal|firing': 'Termination procedures are in accordance with company policy and legal regulations. Employees are given notice as per their contract and local laws.',
        r'work-from-home equipment|home office setup|equipment policy': 'The company provides essential equipment for remote work upon request and approval. Employees are responsible for maintaining their home office setup.',
        r'travel policy|business trips|travel expenses': 'Business travel is subject to approval and reimbursement of expenses as per company policy. Travel guidelines are provided before each trip.',
        r'workplace safety|safety procedures|health and safety': 'We prioritize workplace safety and follow strict health and safety procedures. Regular training is provided to ensure compliance with safety standards.',
        r'equal opportunity|diversity and inclusion|non-discrimination': 'We are committed to providing equal employment opportunities and fostering a diverse and inclusive work environment.',
        r'flexible working hours|flex-time|work schedule': 'Flexible working hours are available with manager approval. Employees can request adjustments to their work schedule as needed.'
    }

    user_input = user_input.lower()
    for pattern, response in responses.items():
        if re.search(pattern, user_input):
            return response

    return 'Sorry, I did not understand that.'
    """
    st.code(code, language='python')

    # User input
    user_input = st.text_input("You:", "")

    if user_input:
        response = chatbot_response(user_input)
        st.text_area("Chatbot:", value=response, height=100, max_chars=None, key=None)

if __name__ == "__main__":
    main()
