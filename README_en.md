### Tetris

Tetris represents an educational game designed for the acquisition of programming skills, wherein players manipulate blocks to compete for scores.

**Resources:**
- Frequently Asked Questions (FAQ) can be accessed here.
- The tutorial is available here.
- The Tetris score server can be found here.
- The Tetris battle server is accessible here.

---

### Preparing the Execution Environment

**Mac Environment**
To initiate the terminal, navigate through Finder → Applications → Utilities → Terminal and execute the following commands. Upon successful installation, the game can be initiated by invoking the specified method.

```bash
# Install pyqt5 and NumPy
brew install python3
brew install pyqt5
brew install numpy

# Install additional packages
brew install git
```

Detailed procedures are documented in `doc/files/install_mac.md`.

**Windows Environment**
Steps to establish a Tetris environment utilizing Windows PowerShell, Windows Subsystem for Linux (WSL), and Docker for Windows are provided.

**Ubuntu/JetsonNano Environment**
Procedures are outlined in `doc/files/install_ubuntu.md`.

**Docker Environment**
Instructions are available in `docker/README.md`.

---

### Execution Instructions

1. **Clone the repository**
   ```bash
   cd $HOME
   git clone https://github.com/seigot/tetris
   ```
   
2. **Start the game**
   ```bash
   cd tetris
   python start.py
   ```

![Screenshot](doc/pics/screenshot_02.png)

---

### Sample Code
To perform a score attack, execute the sample code with the following options:
Refer to the sample program for block operation for detailed information.

```bash
python start.py -m sample
```

**Manual Operation**
To conduct manual operations, the following command options may be specified. Two operational modes are available: PC compliant and game console controller compliant.

| Manual Operation | PC Operation-Compliant | Game Console Controller-Compliant |
|------------------|------------------------|------------------------------------|
| Execution Command | python start.py -m keyboard | python start.py -m gamepad |
| Up Key           | Rotate                  | Fall                              |
| Left Key         | Move left               | Move left                         |
| Right Key        | Move right              | Move right                        |
| M Key            | Move down               | Move down                         |
| Space Key        | Fall                    | Rotate                            |
| P Key            | Pause                   | Pause                             |
| C Key            | Hold                    | Hold                              |

When executed with the `--nextShapeMode hate` option, the game will enter hate mode (for manual operation).

```bash
python3 start.py -m keyboard --nextShapeMode hate
```

---

### AI Implementation
Execution methods and sample code are available. For further details, please consult the section on AI.

**Art**
Execution methods and sample code are provided. For additional details, refer to the section on art.

**Automatic Evaluation Server**
A title server has been prepared by volunteers and is accessible at:  
[GitHub Repository](https://github.com/ChallengeClub/tetris_score_server)

---

### Gameplay Rules
Scores are evaluated based on points accrued within a specified time limit.

**Scoring System**

**Points Added**

| Item                | Score      | Notes |
|---------------------|------------|-------|
| 1 line cleared      | +100 points | -     |
| 2 lines cleared     | +300 points | -     |
| 3 lines cleared     | +700 points | -     |
| 4 lines cleared     | +1300 points | -     |
| Fall bonus          | + (number of falling blocks) | - |
| All clear bonus     | + (points when all cleared) | - |

**Points Subtracted**

| Item                | Score      | Notes |
|---------------------|------------|-------|
| Game over           | -500 points | Game over if the field is filled when blocks appear |

Game levels can be specified with the following options:

| Level   | How to Run                                  | Time Limit   | Block Order                       | Initial Block in Field | Frame Update Frequency                                  | All Clear Bonus |
|---------|---------------------------------------------|--------------|-----------------------------------|------------------------|-------------------------------------------------------|------------------|
| Level 1 | python start.py                             | 180 seconds  | Fixed (1-7 are repeated in order) | None                   | Approx. 1 second                                        | +500             |
| Level 2 | python start.py -l2                        | 180 seconds  | Random                            | None                   | Approx. 1 second                                        | +500             |
| Level 3 | python start.py -l3                        | 180 seconds  | Random                            | Yes                    | Approx. 1 second                                        | +4000            |
| Level 4 | python start.py -l4                        | 180 seconds  | Random                            | Yes                    | Approx. 0.001 seconds                                   | +4000            |

**File Structure**
- **List of Files**
  - `game_manager/game_manager.py`: Game management program
  - `game_manager/board_manager.py`: Board management program
  - `game_manager/block_controller.py`: Block operation program (this file must be modified to operate blocks).
  - `start.py`: Command to initiate the game

**Details**
The configuration indicates that the block operation program is periodically invoked by the management program, requiring the determination of the next action based on board information.

---

### Code Development Guidelines
**Forking This Repository**
To begin, create or log in to a GitHub account and fork this repository into your local storage.

1. Access the repository at: [GitHub Tetris Repository](https://github.com/seigot/tetris)
2. Click the "Fork" button located in the top-right corner of the page.
3. Clone the forked repository to your local machine:

```bash
cd ~
git clone https://github.com/<yourname>/tetris # Replace <yourname> with your account name
```
To delete an existing Tetris directory, execute:

**For Ubuntu/Mac:**
```bash
sudo rm -rf tetris
```

**For Windows PowerShell:**
```bash
Remove-Item -Recurse -Force tetris
```

After obtaining the repository, proceed to update the source code and reflect the changes.

---

### Binary Release
When submitting the binary of the repository, it is advisable to utilize the GitHub release function for ease of management.

**Reference Steps for Submitting Code (Binary Release)**
- Manage repository releases by selecting binary files manually in the release settings.

Future updates to this repository are anticipated. To import updates, run the following commands in your forked repository (As of May 2021, operations can potentially be conducted via the GitHub UI):

```bash
git checkout master # Switch to the local main branch
git remote add upstream https://github.com/seigot/tetris # Register the original repository as upstream
git fetch upstream # Fetch the latest code from upstream
git merge upstream/master # Merge upstream changes into local master
git push # Apply the changes
```

**Optional Pull Request Submission**
Suggestions for revisions to this repository are welcomed. Please refer to related documentation for details on the pull request process.

![Git Commentary](doc/pics/20230115_Git_Commentary.png)
---

### FAQ
Please consult `doc/files/FAQ.md` for further inquiries.

### References
- [LoveDaisy Tetris Game Repository](https://github.com/LoveDaisy/tetris_game)
- [Seigot Tetris Game Repository](https://github.com/seigot/tetris_game) (used until December 2021)
- [Zetcode PyQt5 Tetris Tutorial](http://zetcode.com/gui/pyqt5/tetris/)
- Explore the historical evolution of Tetris through its rules.

### Future Challenges
- Addressing the randomness of the following block via optimized selection methods.
- Introducing competitive elements such as rule updates for AI learning and firepower bonuses.
- Incorporating learning components, including grammar, algorithms, and AI elements.

### License
MIT License.

---

Finally, enjoy the experience!
