# Vaccum-Cleaner-Agent
import random

class VaccumCleaner:
  def __init__(self):
    # clean = 0, dirty = 1
    self.environment = {
        'A': random.randint(0, 1),
        'B': random.randint(0, 1)
    }

    print(f"Initial Environment State: {self.environment}")

    # Place the vaccum cleaner randomly
    self.location = random.choice(['A','B'])
    print(f"Vaccum Cleaner Placed at {self.location}")

    self.path_cost = 0

  def run_agent(self):
    for _ in range(4):
      if self.environment['A'] == 0 and self.environment['B'] == 0:
        print("\n Both Rooms are cleaned and our GOAL is achieved")
        break

      current_status = self.environment[self.location]

      if current_status == 1:
        self.clean()
      else:
        self.move()

      print(f"\nFinal Environment State: {self.environment}")
      print(f"Path Cost: {self.path_cost}")

  def clean(self):
    print(f"Location {self.location} is dirty. ACTION: CLEAN")
    self.environment[self.location] = 0
    self.path_cost += 1
    print(f"Location {self.location} is cleaned. COST +1")

  def move(self):
    print(f"Location {self.location} is clean. ACTION: MOVE")

    if self.location == 'A':
      self.location = 'B'
    else:
      self.location = 'A'

    self.path_cost += 1
    print(f"MOVED TO LOCATION {self.location}. COST +1")

def main():
  agent = VaccumCleaner()
  agent.run_agent()

if __name__ == "__main__":
  main()
