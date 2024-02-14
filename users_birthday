from collections import defaultdict
import datetime

def get_birthdays_per_week(users):
    
    birthdays_per_week = defaultdict(list)
    today = datetime.datetime.today().date()
    days_of_week = ['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday', 'Saturday', 'Sunday']
    
    for user in users:
        name = user["name"]
        birthday = user['birthday'].date()
        birthday_this_year = birthday.replace(year = today.year)
        
        if birthday_this_year < today:
            birthday_this_year = birthday_this_year.replace(year=today.year + 1)
        
        delta_days = (birthday_this_year - today).days
        
        if 0 <= delta_days <= 7:
            day_of_week = birthday_this_year.strftime('%A')
            if day_of_week in ['Saturday', 'Sunday']:
                day_of_week = 'Monday'
                
            birthdays_per_week[day_of_week].append(name)
    
    if 'Saturday' in birthdays_per_week or 'Sunday' in birthdays_per_week:
        birthdays_per_week['Monday'].extend(birthdays_per_week.pop('Saturday', []) + birthdays_per_week.pop('Sunday', []))
        
    for day, birthdays in birthdays_per_week.items():
        print(f"{day}: {', '.join(birthdays)}")    

users = [
    {"name": "Artem", "birthday": datetime.datetime(2001, 2, 15)},
    {"name": "Danilo", "birthday": datetime.datetime(1996, 2, 21)},
    {"name": "Taras", "birthday": datetime.datetime(2003, 2, 28)},
    {"name": "Oleh", "birthday": datetime.datetime(1980, 2, 4)},
    {"name": "Igor", "birthday": datetime.datetime(2000, 2, 10)}
]

get_birthdays_per_week(users)