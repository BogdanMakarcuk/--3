const WIDTH: usize = 30;
const HEIGHT: usize = 15;

fn main() {
    let mut envelope = vec![vec![' '; WIDTH]; HEIGHT];
    
    // Малюємо верхню і нижню рамку
    for x in 0..WIDTH {
        envelope[0][x] = '*';
        envelope[HEIGHT - 1][x] = '*';
    }
    
    // Малюємо бокові сторони
    for y in 0..HEIGHT {
        envelope[y][0] = '*';
        envelope[y][WIDTH - 1] = '*';
    }
    
    // Малюємо діагоналі
    for i in 1..HEIGHT / 2 {
        envelope[i][i * 2] = '*';
        envelope[i][WIDTH - 1 - (i * 2)] = '*';
        envelope[HEIGHT - 1 - i][i * 2] = '*';
        envelope[HEIGHT - 1 - i][WIDTH - 1 - (i * 2)] = '*';
    }
    
    // Виводимо конверт одним print!
    print!("{}
", envelope.iter().map(|row| row.iter().collect::<String>()).collect::<Vec<String>>().join("\n"));
}
