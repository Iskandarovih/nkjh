# nkjhimport sqlite3
from datetime import datetime

# Manage relationship milestones
def add_relationship_milestone(name, date, milestone, db_name='relationship_milestones.db'):
    """
    Add a relationship milestone to the database.

    Parameters:
    - name (str): The name of the person or couple.
    - date (str): The date of the milestone.
    - milestone (str): The description of the milestone.
    - db_name (str): The name of the database file.
    """
    conn = sqlite3.connect(db_name)
    cursor = conn.cursor()
    cursor.execute('''
    CREATE TABLE IF NOT EXISTS milestones (
        id INTEGER PRIMARY KEY,
        name TEXT,
        date TEXT,
        milestone TEXT
    )
    ''')
    cursor.execute('''
    INSERT INTO milestones (name, date, milestone) VALUES (?, ?, ?)
    ''', (name, date, milestone))
    conn.commit()
    conn.close()

# Get all relationship milestones from the database
def get_all_milestones(db_name='relationship_milestones.db'):
    """
    Retrieve all relationship milestones from the database.

    Parameters:
    - db_name (str): The name of the database file.

    Returns:
    - list: A list of tuples containing milestone data.
    """
    conn = sqlite3.connect(db_name)
    cursor = conn.cursor()
    cursor.execute('SELECT * FROM milestones')
    milestones = cursor.fetchall()
    conn.close()
    return milestones

# Example usage of relationship management functions
add_relationship_milestone('John and Jane', '2023-05-15', 'First Date')
milestones = get_all_milestones()
for milestone in milestones:
    print(milestone)

# Create database for cryptocurrency events
def create_crypto_events_database(db_name='crypto_events.db'):
    """
    Create a SQLite database for cryptocurrency events.

    Parameters:
    - db_name (str): The name of the database file.
    """
    conn = sqlite3.connect(db_name)
    cursor = conn.cursor()
    cursor.execute('''
    CREATE TABLE IF NOT EXISTS events (
        id INTEGER PRIMARY KEY,
        date TEXT,
        event TEXT,
        description TEXT
    )
    ''')
    conn.commit()
    conn.close()

# Add an event to the cryptocurrency events database
def add_crypto_event(date, event, description, db_name='crypto_events.db'):
    """
    Add an event to the cryptocurrency events database.

    Parameters:
    - date (str): The 
