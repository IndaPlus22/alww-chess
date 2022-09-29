# alww-chess

rust chess engine

The following public functions are implemented under the public struct Game:
|Function| Description|
|-----------|-------------|
|pub fn new() -> Game | Initialises a new game. Due to me being a [redacted] this will need to be followed by init_bitboard() and update_occupancy() [example init](img/init.png)|
|pub fn init_bitboard(&mut self) | Reset all the bitboards and sets the starting position. |
|pub fn update_occupancy(&mut self) | Updates the occupancies bitboards by synchronizing them with the regular bitboards |
|pub fn make_move(&mut self, &str ) | Moves a piece. The string is formatted as follows: "(From)(To)(Optional: Promotion Piece)". Example "E2E3", from E2 to E3 no promotion piece needed. Example PAWN "E7E8Q", from E7 to E8, promote to QUEEN|
|pub fn set_promotion(&mut self, piece: &str) -> () | Removed. Promotions are made inline with the make_move() function. See examples|
|pub fn get_game_state(&self) -> GameState |Get the current game state.|
|pub fn get_turn(&mut self) -> usize |Returns a bit which represents who's turn it is. If 0 it is White, if 1 it is Black|
|pub fn get_possible_moves(&self) -> <Vec<LocalMove>>| Returns all legal moves for the current board. See public struct LocalMove|

The following public functions are implemented under the public struct LocalMove:
|Function| Description|
|-----------|-------------|
|pub fn get_move_source(&self) -> usize | Returns the source_square of a move, for example if the move was A2 -> A4, the source_square would be A2|
|pub fn get_move_target(&self) -> usize | Returns the target_square of a move, for example if the move was A2 -> A4, the source_square would be A4|
|pub fn get_move_piece(&self) -> usize | Returns the value of the piece making the move, see public struct Pieces|
|pub fn get_move_promoted(&self) -> usize | Returns the value of the pieces that the moving pieces is promoting to|
|pub fn get_move_capture_flag(&self) -> usize | Returns a bit which is the capture flag which determines if a move is quiet or a capturing move|
|pub fn get_move_double_push_flag(&self) -> usize | Returns a bit which is the double pawn push flag which determines if the pawn takes 1 or 2 "steps"|
|pub fn print(&self) | Prints out all of the above.|

LocalMove is used exclusively to store moved more efficiently.

The following public const are implemented under the public struct Pieces:
|Const| Value|
|-----------|-------------|
|const PAWN: usize | 0|
|const BISHOP: usize | 1|
|const KNIGHT: usize | 2|
|const ROOK: usize | 3|
|const QUEEN: usize | 4|
|const KING: usize | 5|
|const pawn: usize | 6|
|const bishop: usize | 7|
|const knight: usize | 8|
|const rook: usize | 9|
|const queen: usize | 10|
|const king: usize | 11|

The following public values are implemented under the public enum GameState:
|Value| Description|
|-----------|-------------|
|InProgress| Works|
|Check| Works|
|GameOver| Broken, as checkmates are not calculated it is very hard to know when it is game over|

| Known bugs: | Description                                                                                                                                     |
| ----------- | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| Checkmate   | It is still possible to checkmate and since this means that there are no legal moves the game will stop/ a player will be unable to do anything |

| Tests |
| ----- |

|![tests][img/tests.png]|
