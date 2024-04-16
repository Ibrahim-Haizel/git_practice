Hello Git and Github

from dash import html

radio_buttons = html.Div([
    html.Div(className='govuk-form-group', children=[
        html.Fieldset(className='govuk-fieldset', children=[
            html.Legend(className='govuk-fieldset__legend govuk-fieldset__legend--s', children='Do you want to accept functional cookies?'),
            html.Div(className='govuk-radios', children=[
                html.Div(className='govuk-radios__item', children=[
                    html.Input(
                        className='govuk-radios__input', 
                        id='cookies-functional', 
                        name='cookies[functional]', 
                        type='radio', 
                        value='yes'
                    ),
                    html.Label(
                        className='govuk-label govuk-radios__label', 
                        htmlFor='cookies-functional', 
                        children='Yes'
                    )
                ]),
                html.Div(className='govuk-radios__item', children=[
                    html.Input(
                        className='govuk-radios__input', 
                        id='cookies-functional-2', 
                        name='cookies[functional]', 
                        type='radio', 
                        value='no',
                        checked=True
                    ),
                    html.Label(
                        className='govuk-label govuk-radios__label', 
                        htmlFor='cookies-functional-2', 
                        children='No'
                    )
                ])
            ])
        ])
    ])
])